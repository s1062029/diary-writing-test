# diary-writing-test
#include <iostream>
#include <fstream>
#include <string.h>
using namespace std;

class dnode{
	public:
	int id;
	char date[20];
	char info[100];
	dnode *next;
};


class abc{
	public:
	char info[100];
	char name[100];
	char date[100];
		int asking()
{
	
	cout<<"請輸入要存的檔案名稱 \n";
	cin>>name;
	
	cout<<"請輸入日期 yyyy-mm-dd \n";
	cin>>date;
	
	cout<<"請輸入你要打的內容 \n";
	cin>>info;
}
		int writefile()
{
	fstream file;
	strcat (date,"\n");
	size_t num=strlen(info);
	size_t num2=strlen(date);
	file.open(name, ios::app); 
	file.write(info,num);
	file.write(date,num2);
	 
	file.close();
 } 
		int openfile()
{
	fstream file;
	cout<<"請輸入要讀的檔案名稱 \n";
	cin>>name;
	
	file.read (info,sizeof(info));
	file.read (date,sizeof(date)); 	
	file.close();

	file.open(name, ios::in) ;
	while(file.getline(info,sizeof(info),','))
	{
	cout<<info<<endl;
	}

	
	file.open (name,ios::in) ;
	for(int i=0;i<10;i++)
	{
		info[i]=info[i]-3;
	}


	exit(1);
}
		int code()
 {
 	for(int i=0;i<10;i++)
	{
		info[i]=info[i]+3;
	}
}
		int askagain()
{
	cout<<"要再寫一篇嗎?輸入Y/N \n";
	char keep;
	cin>>keep;
	if(keep=='Y'or keep=='y')
	{
	cout<<"程式再一次 \n";
	return 1;	
	}
	else if(keep=='N' or keep=='n')
	{
	cout<<"程式結束 \n";
	exit(1);
	}
	else
	{
	cout<<"錯誤 \n";
	}
}
		int catalog()
{
	cout<<"歡迎進入寫日記系統，寫了日記後就準備被看光光吧廠廠~\n";
	cout<<"請選擇你要做的選項\n";
	cout<<"(1) 寫日記 (2) 讀日記 (3) 離開\n";
	
	char chose;
	cin>>chose;
	if(chose=='1')
	{
	do{
	asking();
	writefile();
	code();
	}while(askagain());
	}
	else if(chose=='2')
	{
	do{
	openfile();
	}
	while(askagain());
	}
	else if(chose=='3')
	{
	exit(1);
	}
}
};

void node_load{
}

int main()
{	
	abc s;
	do{
	s.catalog();
	s.asking();
	s.writefile();
	s.code();
	}
	while(s.askagain());	
} 
