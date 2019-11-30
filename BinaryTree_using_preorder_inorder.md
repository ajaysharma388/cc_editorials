Editorial: 💡 Create tree ( Using preorder and inorder)
X
Algorithm:

1) Pick an element from Preorder. Increment a Preorder Index Variable (preIndex in below code) to pick next element in next recursive call.
2) Create a new tree node tNode with the data as picked element.
3) Find the picked element’s index in Inorder. Let the index be inIndex.
4) Call buildTree for elements before inIndex and make the built tree as left subtree of tNode.
5) Call buildTree for elements after inIndex and make the built tree as right subtree of tNode.
6) return tNode.

Lang - Cpp

//Rajkishor Ranjan
// Create Tree for Prefix and Infix Expression.

#include <iostream>
#include <queue>
#include <vector>
using namespace std;

class Node{
public:
    int data;
    Node *left;
    Node* right;
    Node()
    {
        left = NULL;
        right = NULL;
    }

    Node(int n){
        data = n;
        left = NULL;
        right = NULL;
    }
    // friend ostream& operator<<(ostream& writer, Node * root);
};



Node* takeInput(){
    //take input to construct a Binary Tree --depth wise
    int data;
    cin >> data;

    if(data == -1){
        return NULL;
    }

    Node * root = new Node(data);
    root->left = takeInput();   //take input for left SUBTREE 
    root->right = takeInput();
}

Node * takeInputLevel(){
    //function to take Input as a tree --levelwise
    int data;
    cin >> data;
    if (data == -1) return NULL;

    Node * root = new Node(data);
    queue<Node*> q;
    q.push(root);

    while(!q.empty()){
        //there is a node with potential to become parent
        Node *curParent = q.front();
        q.pop();

        int leftData;   cin >> leftData;
        //left child exists, hence create and attach to the parent
        //Also, this child can become Parent in the near future ;)
        if (leftData != -1){
            Node * tmp = new Node(leftData);
            curParent->left = tmp;
            q.push(tmp);
        }

        //similarly for right child
        int rightData;  cin >> rightData;
        if(rightData != -1){
            Node * tmp = new Node(rightData);
            curParent->right = tmp;
            q.push(tmp);
        }
    }
    return root;
}


void printLevel(Node * root){
    queue<Node * > q;
    q.push(root);
    q.push(NULL);

    while(q.empty() == false){
        //I have atleast one node to print
        Node* cur = q.front();
        q.pop();

        //delimiter case
        if(cur == NULL){
            cout << endl;
            if (!q.empty()){
                q.push(NULL);
            }
            continue;
        }


        cout << cur->data << " ";
        if (cur->left) q.push(cur->left);
        if (cur->right) q.push(cur->right);
    }
}


void print(Node* root){
    //preorder Traversal --> root left right
    if (root == NULL) return;

    cout << root->data << " ";
    print(root->left);
    print(root->right);
}

void inorder(Node* root){
    //inorder--> left root right
    if (root == 0)  return;

    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

void postOrder(Node* root){
    //postorder --> left right root
    if (root == 0)  return;

    postOrder(root->left);
    postOrder(root->right);
    cout << root->data << " ";
}

ostream& operator<<(ostream& writer, Node* root){
    //The call is resolved like operator<<(cout, root)-->signature matching
    //all data members of root are public; so can be accessed outside the class
    printLevel(root);
    return writer;
}

istream& operator>>(istream& is, Node*& root){
    root = takeInputLevel();
    return is;
}


int sumTree(Node * root){
    //sumTree UPDATES the tree
    //RETURNS the sum of ORIGINAL tree

    if (root == NULL){
        return 0;
    }

    int left = sumTree(root->left); //get the sum of left SUBTREE; also update it
    int right = sumTree(root->right);
    int sumtoSend = left + right + root->data;
    //the sum of ORIGINAL TREE before updation
    root->data = left + right;
    return sumtoSend;
}

void takeInput2( Node *root )
{
    cin >> root -> data;

    char str[10];

    cin >> str;

    if( str[0] == 't' )
    {
        root -> left = new Node;
        takeInput2( root -> left );
    }

    cin >> str;

    if( str[0] == 't' )
    {
        root -> right = new Node;
        takeInput2( root -> right );
    }

}


using namespace std;

int find( int arr[] , int elem)
{
    int index = 0;

    while( arr[index] != elem )
    {
        index++;
    }

    return index;
}

Node *createTreeI( int preorder[] , int inorder[] , int beg , int en )
{
    if( beg > en ) return NULL;

    static int i = 0;

    Node *root = new Node;
    root -> data = preorder[i++];

    int location = find( inorder , root -> data);

    root -> left = createTreeI( preorder , inorder , beg , location - 1 );
    root -> right = createTreeI( preorder , inorder , location + 1 , en );

    return root;

}

void printDiff( Node *root )
{
    if( !root ) return;

    if( root -> left )
    {
        cout << root -> left -> data << " ";
    }
    else
    {
        cout << "END ";
    }

    cout << "=>";

    cout << " " << root -> data << " ";

    cout << "<=" ;
    if( root -> right )
    {
        cout << " " << root -> right -> data << " ";
    }
    else
    {
        cout << " END";
    }

    cout << "\n";

    printDiff(root -> left );
    printDiff(root -> right);
}

int main()
{
    int size;
    int preorder[50],inorder[50];

    cin >> size;

    for( int i = 0 ; i < size ; i++ )
    {
        cin >> preorder[i];
    }

    cin >> size;

    for( int i = 0 ; i < size ; i++ )
    {
        cin >> inorder[i];
    }

    Node *tree = createTreeI( preorder , inorder , 0 , size - 1);
    printDiff(tree);
    return 0;
}
Lang - Java

private Node construct(int[] pre, int plo, int phi, int[] in, int ilo, int ihi) {
         if (plo > phi) {

            return null;

        }

        Node nn = new Node();
        nn.data = pre[plo];

        int j = 0;
        for (int i = ilo; i <= ihi; i++) {
            if (in[i] == pre[plo]) {
                j = i;
                break;
            }
        }

        nn.left = construct(pre, plo + 1, plo + j - ilo, in, ilo, j - 1);
        nn.right = construct(pre, plo + 1 + j - ilo, phi, in, j + 1, ihi);

        return nn;
        }