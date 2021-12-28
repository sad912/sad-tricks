# 在 win11 中设置小鹤双拼

通过修改注册表的方式来添加小鹤双拼的方案。

1. 新建reg文件；
2. 粘入下述设置
```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\SOFTWARE\Microsoft\InputMethod\Settings\CHS]
"EnableExtraDomainType"=dword:00000001
"Enable Double Pinyin"=dword:00000001
"DoublePinyinScheme"=dword:0000000a
"UserDefinedDoublePinyinScheme0"="小鹤双拼*2*^*iuvdjhcwfg^xmlnpbksqszxkrltvyovt" 
```
3. 在输入法的双拼方案里设置新建的方案。