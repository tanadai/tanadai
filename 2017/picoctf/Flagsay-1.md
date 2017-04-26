# LEVEL2:Flagsay 1
ソースコードを読むと以下の部分があり, System関数でコマンドを実行していることからコマンドインジェクションが使えるのではと予測できる.
````
char commandBase[] = "/bin/echo \"%s\"\n";
````
よって``" ; cat flag.txt"``でflagが得られる.	