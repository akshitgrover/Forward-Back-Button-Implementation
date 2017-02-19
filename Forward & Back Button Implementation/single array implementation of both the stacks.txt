#include<iostream>
#include<stdlib.h>
using namespace std;
class stack_t
{
    public:
    int page[50];
    int fwd;
    int bck=-1;
    int cur_page=1;
};
int main()
{
    int temp_page,choice;
    stack_t s_arr;
    s_arr.fwd=s_arr.bck;
    if(s_arr.cur_page==1)
    {
        cout<<"You Are Currently At Homepage"<<endl<<endl;
        cout<<"Enter Page Number To Visit: ";
        cin>>temp_page;
        s_arr.fwd++;
        s_arr.bck++;
        s_arr.page[s_arr.bck]=s_arr.cur_page;
        s_arr.cur_page=temp_page;
        system("CLS");
    }
    while(1)
    {
        cout<<"You Are On Page: "<<s_arr.cur_page<<endl<<endl;
        cout<<"To Go To Previous Page *Press 1, To Go To Forward Page *Press 2, To Visit Page Of Your Choice *Press 3, To Exit *Press 0"<<endl;
        cin>>choice;
        if(choice==1)
        {
            if(s_arr.bck!=-1)
            {
                s_arr.fwd++;
                s_arr.page[s_arr.fwd]=s_arr.cur_page;
                s_arr.cur_page=s_arr.page[s_arr.bck];
                for(int i=s_arr.bck+1;i<=s_arr.fwd;i++)
                {
                    s_arr.page[i-1]=s_arr.page[i];
                }
                s_arr.bck--;
                s_arr.fwd--;
                system("CLS");
            }
            else
            {
                system("CLS");
            }
        }
        if(choice==2)
        {
            if(s_arr.fwd!=s_arr.bck)
            {
                for(int i=s_arr.fwd;i>s_arr.bck;i--)
                {
                    s_arr.page[i+1]=s_arr.page[i];
                }
                s_arr.fwd++;
                s_arr.bck++;
                s_arr.page[s_arr.bck]=s_arr.cur_page;
                s_arr.cur_page=s_arr.page[s_arr.fwd];
                s_arr.fwd--;
                system("CLS");
            }
            else
            {
                system("CLS");
            }
        }
        if(choice==3)
        {
            system("CLS");
            cout<<"Enter Page Number To Visit: ";
            cin>>temp_page;
            for(int i=s_arr.fwd;i>s_arr.bck;i--)
            {
                s_arr.page[i+1]=s_arr.page[i];
            }
            s_arr.fwd++;
            s_arr.bck++;
            s_arr.page[s_arr.bck]=s_arr.cur_page;
            s_arr.cur_page=temp_page;
            system("CLS");
        }
        if(choice==0)
        {
            return 0;
        }
    }
    return 0;
}
