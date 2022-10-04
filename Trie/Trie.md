# Trie data structure

* It is tree like data structure.
* Like hash map It is mainly used in information retrieval.
* It is also known as prefix tree.

```
String[] ["mango", "apple", "ape", "no", "not", "news", "code"]
```

* Lets assume wants to search "not" in that case it will take O(mn) considering ``m`` is size of array and ``n`` is size of string.
* But trie will take time O(n). i.e time taken will be proportinal to the length or size of the word to be searched.

* Here in case of trie space complexity will increase+precomputation.

```
                            (-)
                            /\
                          (a) (n)--\   
                          /     \    \
                        (p)     [(o)] (e)
                        /  \       \     \
                      (p)   [(e)]   [(t)] (w)
                      /                    \
                    (l)                     [(s)]
                    /
                  [(e)]  


All the nodes in [] are terminal nodes.

```

```C
#include<iostream>
#include<unordered_map>
using namspace std;
#define hashmap unordered_map<char node *>

class node{
    public:
        char data;
        hashmap h;
        bool isTerminal;

        node(char d)
        {
            data=d;
            isTerminal=false;
        }
};

class Trie
{
    node * root;

    public:
    Trie()
    {
        root=new node("\0")
    }
//insetion
    void addWord(char * word)
    {
        node * temp=root;
        for(int i=0;i<word[i]!="\0";i++)
        {
            char ch=word[i];
            if(temp->h.count(ch)==0)
            {
                node * child=new node(ch);
                temp->h[ch]=child;
                temp=child;
            }
            else
            {
                temp=temp->h[ch];
            }
        
        }
        temp->isTerminal=true;
    }
}

//lookup

bool isPresent(char *word)
{
    node *temp;
    for(int i=0;word[i]!='\0';i++)
    {
        char ch=word[i];
        if(temp->h.count(word[i]))
        {
            temp=temp->h[ch];
        }
        else
        {
            return false;
        }
    }

    return temp->isTerminal;

}


void main()
{
    char word[10][100]={"apple","ape","coder","coding", "no"};

    Trie t;
    for(int i=0;i<5;i++)
    {
        t.addWord(word[i]);
    }

    char searchWord[100];
    cin.getline(searchWord,100);
    if(t.search(searchWord))
    {
        cout<<searchWord<<" found "<<endl;
    }
    else
        cout<<"not found !"<<endl;
}


```



---------------------------------------End of Document---------------------------------------

