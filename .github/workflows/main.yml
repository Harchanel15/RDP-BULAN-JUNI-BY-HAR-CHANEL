name: Har Pito
on: workflow_dispatch
jobs:
  build:
    runs-on: windows-latest
    timeout-minutes: 9999
    steps:
    - name: Download Ngrok.
      run: |
        Invoke-WebRequest https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-windows-amd64.zip -OutFile ngrok.zip
        Invoke-WebRequest https://raw.githubusercontent.com//Harchanel15/REPO-BULAN-MARET-BY-HAR-CHANEL/main/start.bat -OutFile start.bat
        Invoke-WebRequest https://raw.githubusercontent.com/Harchanel15/REPO-BULAN-MARET-BY-HAR-CHANEL/main/download.jpeg -OutFile wallpaper.bat
        Invoke-WebRequest https://raw.githubusercontent.com/Harchanel15/REPO-BULAN-MARET-BY-HAR-CHANEL/main/loop.bat -OutFile loop.bat
    - name: Extract Ngrok File.
      run: Expand-Archive ngrok.zip
    - name: Connect Ngrok.
      run: .\ngrok\ngrok.exe authtoken $Env:NGROK_AUTH_TOKEN
      env:
        NGROK_AUTH_TOKEN: ${{ secrets.NGROK_AUTH_TOKEN }}
    - name: Windows10 RDP.
      run: |
        Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server'-name "fDenyTSConnections" -Value 0
        Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
        Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 1
        copy wallpaper.bat D:\a\wallpaper.bat
    - name: Tunnel.
      run: Start-Process Powershell -ArgumentList '-Noexit -Command ".\ngrok\ngrok.exe tcp --region ap 3389"'
    - name: Connect Rdp.
      run: cmd /c start.bat
    - name: win10 RDP.
      run: cmd /c loop.bat
