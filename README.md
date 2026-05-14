# Auto Spotifyd Build for Windows

> [!Note]
> Spotifyd requires a Spotify Premium account.

This repository provides a Windows binary that is *automatically* compiled whenever a new version is released in the original project.

> [!Warning]
> Although the project is called “Auto Spotify Build for Windows,” the process (at least for now) isn't really that automatic. Until I can set up a good GitHub Actions workflow, I'll have to do this manually... But since the project's last build was more than... a long time ago, it's not a problem for now. lol

Current build based on version **0.4.2**.

Download last release using powershell:

``` ps1
cls;$s="spotifyd";try{echo "Downloading $s...";$r=irm "api.github.com/repos/hppsrc/auto-spotifyd-build-for-windows/releases/latest";$e=$r.assets|where{$_.name -like "*.exe"}|select -First 1;if($null -eq $e){echo "Not Found";return}$d= $e.browser_download_url;mkdir "C:\$s" -ErrorAction SilentlyContinue|Out-Null; curl -# -L $d -o "C:\$s\$s.exe";echo "$s saved on C:\$s\$s.exe`nFile Hash: " $(get-FileHash "C:\$s\$s.exe").hash}catch{Echo "$_"}
```

Please note that to log in, you must use the  `` spotifyd.exe auth `` command.

This may not be the only step required, depending on the program you are using.

Links to the original project and more:
- [Spotifyd Website](https://spotifyd.rs)
- [Spotifyd GitHub repo](https://github.com/Spotifyd/spotifyd)
- [Spotifyd Wiki](https://spotifyd.github.io/spotifyd/)
