---
layout: default
title: Projelerim
permalink: /my-projects/g4tor
---

<nav>
      <ul style="display: flex;list-style:none">
        {% for item in site.data.menu %}
        <li style="margin-right: 50px"><a style="text-decoration:none" class="{% if page.url == item.link %}active{% endif %}" href="{{ item.link }}">{{ item.title }}</a></li>
        {% endfor %}
      </ul>
</nav>

## My Projects

Bu kısımda github'daki projelerimi açıklayacağım.

```java
public static String randomKey(int length) {
    	System.out.println("[*] Generating a key...");
    	String upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    	String lower = "abcdefghijklmnopqrstuvwxyz";
    	String number = "0123456789";
    	String special = ".,;<>?/[{]}+-_)(*!'^%#$@=";
    	String combined = upper + lower + number + special;
    	String password = "";
    	Random random = new Random();
    	for(int i=0; i<length; i++) {
    		password += combined.charAt(random.nextInt(combined.length()));
    	}
    	System.out.println("[*] Your key is : " + password);
    	System.out.println("[!] Write it from client.");
    	return password;
    }
```

Bu kısımda github'daki projelerimi açıklayacağım.

```java
public static void receiver_mode(String fileName) throws IOException, InterruptedException {
    	
    	System.out.print("[*] Port: ");
		port =  Integer.parseInt(mode.nextLine());
		ServerSocket ss = new ServerSocket(port);
		Socket s = ss.accept();
		DataInputStream din = new DataInputStream(s.getInputStream());
		String str = "";
		key = randomKey(5);
		str = din.readUTF();
		
		if(str.equals(key)) {
			System.out.println("[+] Key accepted. ");
			din.close();
			s.close();
			ss.close();
			System.out.println("[*] Preparing socket for server.");
			Thread.sleep(3000);
			try(ServerSocket serverSocket = new ServerSocket(port)) {  
	            
				if(serverSocket.isBound()) {
					System.out.println("[!] Server socket bounded to Port: " + serverSocket.getLocalPort());
				} else {
					System.out.println("[!] Server socket not bounded.");
				}
	            
	            Socket clientSocket = serverSocket.accept();
	            
	            if(clientSocket.isConnected()) {
	            	System.out.println("[!] Client socket connected: " + clientSocket.getInetAddress());
	            } else {
	            	System.out.println("[!] Client socket not connected.");
	            }
	            
	            dataInputStream = new DataInputStream(clientSocket.getInputStream());
	            dataOutputStream = new DataOutputStream(clientSocket.getOutputStream());

	            try {
	        		FileOutputStream fileOutputStream = new FileOutputStream(fileName);
	            	
	            	int transferred_bytes = 0;
	                long file_size = dataInputStream.readLong();
	                byte[] buffer = new byte[4096];
	                System.out.println(file_size);
	                while (file_size > 0 && (transferred_bytes = dataInputStream.read(buffer, 0, buffer.length)) != -1) {
	                    fileOutputStream.write(buffer, 0, transferred_bytes);
	                    System.out.println("[*] Transferred bytes: " + transferred_bytes);
	                    file_size -= transferred_bytes;
	                }
	                System.out.println("[*] File received.");
	                fileOutputStream.close();
	        	} catch(Exception e) {
	        		e.printStackTrace();
	        	}
	            
	            dataInputStream.close();
	            dataOutputStream.close();
	            clientSocket.close();
	        } catch (Exception e){
	            e.printStackTrace();
	        }
		} else {
			din.close();
			s.close();
			ss.close();
		}
  }
```

Bu kısımda github'daki projelerimi açıklayacağım.

```java
public static void sender_mode(String path) throws UnknownHostException, IOException, InterruptedException {
    	
    	System.out.print("[*] Server address: ");
		address = mode.nextLine();
		System.out.print("[*] Server port: ");
		port =  Integer.parseInt(mode.nextLine());

		Socket keySocket = new Socket(address, port);
		dataOutputStream = new DataOutputStream(keySocket.getOutputStream());
		BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

		String skey = "";
		System.out.print("[!] Key: ");
		skey = bufferedReader.readLine();
		dataOutputStream.writeUTF(skey);

		Thread.sleep(10000);
		try(Socket socket = new Socket(address, port)) {
			
			if(socket.isConnected()) {
				System.out.println("[!] Socket connection established: " + socket.getInetAddress());
			} else {
				System.out.println("[!] Socket connection not established.");
			}
			
            dataInputStream = new DataInputStream(socket.getInputStream());
            dataOutputStream = new DataOutputStream(socket.getOutputStream());

            try {
        		File file = new File(path);
        	       
                if(file.exists()) {
                	System.out.println("[!] File existing.");
                } else {
                	System.out.println("[!] File not existing.");
                }
                
                FileInputStream fileInputStream = new FileInputStream(file);
                dataOutputStream.writeLong(file.length());  
                System.out.println(file.length());
                int transferring_bytes = 0;
                byte[] buffer = new byte[4096];

                while((transferring_bytes=fileInputStream.read(buffer))!=-1){
                    dataOutputStream.write(buffer,0,buffer.length);
                    System.out.println("[*] Transferring bytes: " + transferring_bytes);
                    dataOutputStream.flush();
                }
                System.out.println("[*] File transferred.");
                fileInputStream.close();
        	} catch(Exception e) {
        		e.printStackTrace();
        	}
            
            dataInputStream.close();
	    	dataOutputStream.close();
        }catch (Exception e){
            e.printStackTrace();
        }
		dataOutputStream.close();
		keySocket.close();
    }
```

Bu kısımda github'daki projelerimi açıklayacağım.

```java
public static void main(String args[]) throws IOException, InterruptedException {
		mode = new Scanner(System.in);
		System.out.println("[!] Choose Mode\n[*] 1- Receive\n[*] 2- Send");
		System.out.print("[?] Mode: ");
		
		int mod = Integer.parseInt(mode.nextLine());
		
		switch(mod) {
			case 1:
				receiver_mode("whitepages.txt");
				break;
			case 2:
				sender_mode("whitepages.txt");
				break;
			default:
				break;
		}
	}
```

Projenin Github sayfasına gitmek için aşağıdaki butona basıp gidebilirsiniz.

<button style="background-color: white;color: black;border: 2px solid #4CAF50;width: 250px" href="https://github.com/thealper2/g4tor">Kodun tam haline gitmek için Tiklayiniz</button>

---

<footer style="float:left;"><small>&copy; 2022 thealper2</small></footer>
<footer style="float:right;"><small><a href="https://github.com/thealper2">My Github</a></small></footer>