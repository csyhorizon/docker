```
# 1. 패키지 업데이트 및 필수 도구 설치
sudo apt update && sudo apt install -y zsh curl git wget unzip gnupg software-properties-common

# 2. 테라폼 공식 레포지토리 등록 및 설치
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install -y terraform

# 3. Oh My Zsh 설치 (비대화형 모드)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended

# 4. Zsh 플러그인 설치 (자동완성, 하이라이팅)
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# 5. .zshrc 설정 업데이트 (플러그인 적용)
sed -i 's/plugins=(git)/plugins=(git terraform zsh-autosuggestions zsh-syntax-highlighting)/' ~/.zshrc

# 6. 테라폼 자동완성 설치 명령 예약
terraform -install-autocomplete
```