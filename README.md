請在Ubuntu環境下執行

先打開Ubuntu terminal(切換到想要的資料夾裡面)

# 使用 flex 和 bison 實作編譯器的 「詞法分析」和「語法分析」

安裝 lex(flex) 和 yacc(bison)：  
sudo apt-get install flex  
sudo apt-get install bison
  
  
下載範例C檔：  
git clone https://github.com/Kennnijy/1142_CompilerFinalProject.git

  
進入資料夾：  
cd 1142_CompilerFinalProject
  
  
用 Lex 工具編譯 lex.l ⮕ 產生 lex.y.c：  
lex lex.l  
  
  
用 Yacc 工具編譯 yacc.y  ⮕ 產生 y.tab.c：  
~yacc yacc.y~ (yacc yacc.y 會有錯誤)  
yacc -d yacc.y (所以需要用 yacc -d yacc.y 指令對yacc.y產生標頭檔)  
  
  
編譯 lex.yy.c 和 y.tab.c，產生檔名為 Complie 的可執行檔：  
cc lex.yy.c y.tab.c -o Compile
  
  
編譯.c檔(可自行替換 1~8 不同數字，總共有八個 C 檔)：  
./Compile < sample1.c
  




# 使用 gcc 完成組合語言

下載範例C檔：  
git clone https://github.com/Kennnijy/1142_CompilerFinalProject.git

進入資料夾：  
cd 1142_CompilerFinalProject

-S 代表只編譯到組合語言，-masm=intel 代表使用 Intel 語法風格(可自行替換 1~8 不同數字，總共有八個 C 檔)：  
gcc -S -masm=intel sample5.c -o sample5_gcc.s

查看產生出來的組合語言程式碼
cat sample5_gcc.s

產生執行檔 sample5_gcc_exe：  
gcc sample5.c -o sample5_gcc_exe

執行：  
./sample5_gcc_exe





# 使用 LLVM+Clang 完成完整的編譯過程





# 使用 LLVM+Clang 完成完整的編譯過程 (用腳本執行

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
  
  
執行(setup_compiler.sh 是環境建置；run_pipeline.sh是編譯)：  
./setup_compiler.sh  
./run_pipeline.sh


