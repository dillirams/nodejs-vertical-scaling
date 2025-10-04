# 🚀 Vertical Scaling in Node.js with Cluster Module

JavaScript is a **single-threaded language**.  
No matter how big the application is, it runs on **a single core**, and that single core is responsible for handling all incoming requests.  

### ⚠️ Problem
- Running the application on just one process limits performance.  
- Trying to run the same app on different machines or ports can lead to **port conflicts** and poor scalability.  

### ✅ Solution: Vertical Scaling with Clustering
We can achieve **vertical scaling** by forking the process using Node’s built-in `cluster` module.  
This allows us to utilize **all available CPU cores** in a single machine, making the application more scalable and efficient.

> 💡 In simple terms: Clustering creates **multiple worker processes** (one per CPU core) that share the same server port, allowing Node.js to handle **more requests in parallel** without being stuck on a single thread.

## 🔎 Difference from Multi-threaded Languages

- **Rust, Python, Java, C++** (multi-threaded languages)  
  These languages can natively create and manage multiple threads, allowing them to distribute work across **all available CPU cores**. This makes them highly efficient in parallel processing and computation-heavy tasks.

- **Node.js (single-threaded)**  
  Node.js runs its event loop on a single thread, which means it cannot fully utilize multiple CPU cores by default. Even if your system has 8 cores, Node.js will only use 1 core unless you explicitly scale it.
## 📊 Monitoring CPU Usage

You can use the `htop` command in Linux or macOS to see how your application uses the CPU cores in real time:

```bash
htop