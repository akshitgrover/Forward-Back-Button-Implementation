#include <iostream>
#include <stack>
#include <stdlib.h>
using namespace std;
stack <int> fwd,bck;
int cur_page=1;
int main()
{
    int temp_page,choice;
    if(cur_page==1)
    {
        cout<<"You Are Currently At Homepage"<<endl<<endl;
        cout<<"Enter Page Number To Visit: ";
        cin>>temp_page;
        bck.push(cur_page);
        cur_page=temp_page;
        system("CLS");
    }
    while(1)
    {
        cout<<"You Are On Page: "<<cur_page<<endl<<endl;
        cout<<"To Go To Previous Page *Press 1, To Go To Forward Page *Press 2, To Visit Page Of Your Choice *Press 3, To Exit *Press 0"<<endl;
        cin>>choice;
        if(choice==2)
        {
            if(!fwd.empty())
            {
                bck.push(cur_page);
                cur_page=fwd.top();
                fwd.pop();
                system("CLS");
            }
            else
            {
                system("CLS");
            }
        }
        if(choice==1)
        {
            if(!bck.empty())
            {
                fwd.push(cur_page);
                cur_page=bck.top();
                bck.pop();
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
            bck.push(cur_page);
            cur_page=temp_page;
            system("CLS");
        }
        if(choice==0)
        {
            return 0;
        }
    }
    return 0;
}
