# Compiler sample(腳本執行

請在Ubuntu環境下執行

先打開Ubuntu terminal(切換到想要的資料夾裡面)

接著裝以下這兩個自動安裝與執行腳本擋(*.sh)：  
wget https://raw.githubusercontent.com/Kennnijy/1142_CompilerFinalProject/refs/heads/main/setup_compiler.sh  
wget https://raw.githubusercontent.com/Kennnijy/1142_CompilerFinalProject/refs/heads/main/run_pipeline.sh

調整權限：  
chmod +x setup_compiler.sh  
chmod +x run_pipeline.sh

使用 sed 指令直接把 Windows 的 \r 拔掉 
(在終端機分別輸入這兩行指令，直接用 Linux 的流編輯器把檔案裡的 Windows 換行符號清洗乾淨)：  
sed -i 's/\r$//' setup_compiler.sh    
sed -i 's/\r$//' run_pipeline.sh

執行(兩個檔案需要分開執行)：  
./setup_compiler.sh  
./run_pipeline.sh




# Compiler sample(手動輸入

安裝 lex(flex) 和 yacc(bison)：  
sudo apt-get install flex  
sudo apt-get install bison

下載範例C檔：  
git clone https://github.com/gjlmotea/Compiler-sample.git

進入資料夾：  
cd Compiler-sample/


用 Lex 工具編譯 lex.l ⮕ 產生 lex.y.c：  
lex lex.l  

用 Yacc 工具編譯 yacc.y  ⮕ 產生 y.tab.c：  
~yacc yacc.y~  
yacc -d yacc.y( yacc yacc.y 會有錯誤，需要用 yacc -d yacc.y 指令對yacc.y產生標頭檔)  

cc lex.yy.c y.tab.c -o Compile

編譯(可自行替換
./Compile < sample1.c



















