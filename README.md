
# 市町村の緯度経度情報

[https://ja.exploratory.io/data/GMq1Qom5tS/umM3OCQ8ZD](https://ja.exploratory.io/data/GMq1Qom5tS/umM3OCQ8ZD) からダウンロード

# テキスト ファイルからのデータのインポート

次のテキスト ファイルからデータをインポートするスクリプト:

```
\National Land Information Division\市区町村緯度経度.csv
```

MATLAB からの自動生成日: 2024/10/10 10:53:58

# インポート オプションの設定およびデータのインポート
```matlab
opts = delimitedTextImportOptions("NumVariables", 8);

% 範囲と区切り記号の指定
opts.DataLines = [2, Inf];
opts.Delimiter = ",";

% 列名と型の指定
opts.VariableNames = ["VarName1", "Level1_Name", "Level2_Name", "VarName4", "VarName5", "VarName6", "VarName7", "VarName8"];
opts.VariableTypes = ["double", "categorical", "string", "categorical", "categorical", "categorical", "double", "double"];

% ファイル レベルのプロパティを指定
opts.ExtraColumnsRule = "ignore";
opts.EmptyLineRule = "read";

% 変数プロパティを指定
opts = setvaropts(opts, "Level2_Name", "WhitespaceRule", "preserve");
opts = setvaropts(opts, ["Level1_Name", "Level2_Name", "VarName4", "VarName5", "VarName6"], "EmptyFieldRule", "auto");

% データのインポート
tbl = readtable("市区町村緯度経度.csv", opts)

```
### ラベル
```matlab
%% テキスト ファイルからのデータのインポート
% 次のテキスト ファイルからデータをインポートするスクリプト:
%
%    ファイル名: C:\Users\nakamura\Dropbox\Repository\0_tmp\p2p_program\National Land Information Division\市区町村緯度経度.csv
%
% MATLAB からの自動生成日: 2024/10/10 10:55:57

%% インポート オプションの設定およびデータのインポート
opts = delimitedTextImportOptions("NumVariables", 8);

% 範囲と区切り記号の指定
opts.DataLines = [1, 1];
opts.Delimiter = ",";

% 列名と型の指定
opts.VariableNames = ["VarName1", "Level1_Name", "Level2_Name", "VarName4", "VarName5", "VarName6", "VarName7", "VarName8"];
opts.VariableTypes = ["char", "char", "char", "char", "char", "char", "char", "char"];

% ファイル レベルのプロパティを指定
opts.ExtraColumnsRule = "ignore";
opts.EmptyLineRule = "read";

% 変数プロパティを指定
opts = setvaropts(opts, ["Level1_Name", "Level2_Name", "VarName4", "VarName5", "VarName6"], "WhitespaceRule", "preserve");
opts = setvaropts(opts, ["Level1_Name", "Level2_Name", "VarName4", "VarName5", "VarName6"], "EmptyFieldRule", "auto");

% データのインポート
Untitled = readtable("市区町村緯度経度.csv", opts);

%% 出力型への変換
Untitled = table2cell(Untitled);
numIdx = cellfun(@(x) ~isnan(str2double(x)), Untitled);
Untitled(numIdx) = cellfun(@(x) {str2double(x)}, Untitled(numIdx));

%% 一時変数のクリア
clear numIdx opts

tbl.Properties.VariableNames=cellstr(Untitled);

save("JapanCityLocationData.mat","tbl");
```
