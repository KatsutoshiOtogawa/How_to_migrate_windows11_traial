# How_to_migrate_windows11_traial

Windows11の試用版をwindows 11にTPM, cpuなど対応していないPCに入れる方法。

windows10 or windows serverの試用版を取得する。

これをインストールして
```powershell
# [microsoft official how to install windows11](https://support.microsoft.com/ja-jp/windows/windows-11-%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95-e0edbbfb-cfc5-4011-868b-2ce77ac7c70e)
# HKLM は HKEY_LOCAL_MACHINE のhiveです。 

# 指定のレジストリキーが作成。
if (!(Test-Path HKLM:\SYSTEM\Setup\MoSetup)) {
    New-Item HKLM:\SYSTEM\Setup\MoSetup
    # REG_DWORDでなくてDWORDとなっていますが、間違いじゃありません。[レジストリのデータ型について](https://atmarkit.itmedia.co.jp/fdotnet/dotnettips/120regtype/regtype.html)
    New-ItemProperty HKLM:\SYSTEM\Setup\MoSetup -Name "AllowUpgradesWithUnsupportedTPMOrCPU" -PropertyType DWORD -Value 1
}

```

## 
windows 11 の試用版をダウンロードしてくる。
isoファイルをマウントして、setup.exe

あとはクリーンインストールなりなんなり。