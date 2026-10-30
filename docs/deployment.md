# Deploy to Azure Ubuntu VM with Nginx

Ensure the VM network security group permits inbound TCP port 80 from the intended clients.

```bash
sudo apt update
sudo apt install -y nginx git
sudo systemctl enable --now nginx
```

Clone your own GitHub repository (replace `YOUR_USERNAME`):

```bash
git clone https://github.com/YOUR_USERNAME/royalsignaturewear.git
sudo cp royalsignaturewear/index.html /var/www/html/index.html
sudo nginx -t
sudo systemctl reload nginx
```

Visit `http://YOUR_VM_PUBLIC_IP` to test. To use the domain, configure its DNS A record to point to your VM's stable public IP. For production, configure HTTPS with a valid TLS certificate.

For future updates:

```bash
cd royalsignaturewear
git pull origin main
sudo cp index.html /var/www/html/index.html
sudo systemctl reload nginx
```
