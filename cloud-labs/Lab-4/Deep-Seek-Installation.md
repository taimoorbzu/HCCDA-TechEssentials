# 🚀 DeepSeek Installation Guide on HUAWEI CLOUD using Ollama

This Lab provides a step-by-step guide for deploying the **DeepSeek 1.5B Large Language Model (LLM)** on a **HUAWEI CLOUD Elastic Cloud Server (ECS)** using the **Ollama** framework.

---

## ☁️ Step 1: Prepare the Cloud Environment

Begin by setting up your cloud server:

- **Region**: AP-Singapore  
- **ECS Type**: `c6.xlarge.2` (pay-per-use)  
- **vCPUs**: 4  
- **RAM**: 8 GiB  
- **OS**: CentOS 8.2 (64-bit)

### 🔌 Network Configuration:

- Assign a **public Elastic IP (EIP)**
- Set **bandwidth** to **100 Mbit/s** (recommended for fast downloads)

After creating the ECS, log in using **CloudShell** from the HUAWEI Cloud dashboard.

---

## 🛠️ Step 2: Install Ollama

Ollama is an open-source tool that simplifies running large language models on cloud or local machines.

You can install Ollama in two different ways:

### ✅ Method 1: Online Installation

Run the following command:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### 🛡️ Method 2: Offline Installation via OBS

If you're facing network issues, use this alternative method:

1. **Download** the Ollama package from a **Huawei OBS** bucket.
2. **Decompress** the package:

```bash
tar -xzf ollama.tar.gz
```

3. **Create a system user** for Ollama:

```bash
sudo useradd -r -s /bin/false ollama
```

4. **Set up the systemd service**:

```bash
sudo cp ollama.service /etc/systemd/system/
sudo systemctl daemon-reexec
sudo systemctl enable --now ollama
```

---

## 📦 Step 3: Download and Prepare the DeepSeek Model

There are two options to get the DeepSeek model:

### 🐢 Option 1: Pull from Ollama Registry (Slower)

Use the following command:

```bash
ollama pull deepseek-r1:1.5b
```

> This method can be slow depending on your network speed.

### ⚡ Option 2: Download from OBS (Faster)

1. **Download** the pre-packaged DeepSeek model archive from OBS.
2. **Extract** the archive:

```bash
tar -xzf deepseek-model.tar.gz
```

3. **Move** the model files to Ollama's models directory:

```bash
mv deepseek-model ~/.ollama/models
```

---

## 🧠 Step 4: Run the DeepSeek Model

Start an interactive session with DeepSeek using:

```bash
ollama run deepseek-r1:1.5b
```

This will launch a terminal interface allowing you to interact directly with the DeepSeek language model on your Huawei Cloud ECS.

---

## 📌 Notes

- Make sure all required ports are open if accessing Ollama remotely.
- Use `systemctl status ollama` to check that the service is running.
- Monitor CPU and RAM usage — DeepSeek models may be demanding for production scenarios.

---

## 🎉 Done!

You’ve now successfully:

- Provisioned a Huawei Cloud ECS instance
- Installed Ollama
- Loaded the DeepSeek 1.5B model
- Started an interactive AI session on your own cloud server

You’re ready to build, test, and explore!

(<img width="777" height="560" alt="3" src="https://github.com/user-attachments/assets/5950115c-31d4-45e5-bd41-e6c320dbd738" />
<img width="787" height="425" alt="2" src="https://github.com/user-attachments/assets/32cf1f43-93c5-4268-9ab6-af25966c3770" />
<img width="794" height="489" alt="1" src="https://github.com/user-attachments/assets/549cfc55-e39c-4c68-8d4f-0f269511e29b" />
![WhatsApp Image 2025-07-27 at 20 52 42_c0bad4cd](https://github.com/user-attachments/assets/3795fb9e-2e9b-4ece-82d3-786ba02d4c6c)
<img width="789" height="428" alt="6" src="https://github.com/user-attachments/assets/9640d192-2cc4-4809-b6d6-73b2c7f48afc" />
<img width="788" height="597" alt="5" src="https://github.com/user-attachments/assets/2400bdc3-6bac-4274-9d4d-5b67a652c593" />
<img width="781" height="362" alt="4" src="https://github.com/user-attachments/assets/93915ba3-0b3d-416c-9588-3a413b1fe7b5" />
)
