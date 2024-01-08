# The Expanse: A Telltale Series Epic Store Fix for Steam Deck (VC missing)
This is a simple explanation how to run The Expanse : Telltale Series from Epic Games on Steam Deck.

If you install game from Epic Store (not through Heroic, but with legacy installer) Running game will pop up that there is no VC++ library installed.

To fix this, you need to find game file "Artemis.exe" and replace it with VC_redist installation file.
Now running the game will open VC++ installer in EGS Environment. Just install it, and restore original game file, or reinstall whole game.

You can also use this simple script, just copy and paste it in Steam Deck's Terminal window.:

# Get installer:
```
file_path=$(find /mnt/e/ -name "Artemis.exe" 2>/dev/null)
if [ -z "$file_path" ]; then echo "Artemis.exe not found."; exit 1; fi; cp "$file_path" "${file_path}.bak"; wget -O "$file_path" https://download.visualstudio.microsoft.com/download/pr/a061be25-c14a-489a-8c7c-bb72adfb3cab/4DFE83C91124CD542F4222FE2C396CABEAC617BB6F59BDCBDF89FD6F0DF0A32F/VC_redist.x64.exe
```

# Restore original file:
```
backup_file_path=$(find /mnt/e/ -name "Artemis.exe.bak" 2>/dev/null)
if [ -z "$backup_file_path" ]; then echo "Backup of Artemis.exe not found."; exit 1; fi ; original_file_path="${backup_file_path%.bak}" ;mv "$backup_file_path" "$original_file_path"
```
