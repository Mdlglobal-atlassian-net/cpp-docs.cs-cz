---
title: Ukazatelé (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarators, pointers
- declarations, pointers
- pointers [C++]
- pointers, declarations
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dad1f9a223d8eb97c8e59e955bd5358b27dafd08
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947605"
---
# <a name="pointers-c"></a>Ukazatelé (C++)
Ukazatele jsou deklarovány následujícím způsobem.  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator ;  
```  
  
 kde lze použít libovolný platný ukazatel deklarátor pro `declarator`.  Syntaxe deklarátoru jednoduchého ukazatele je následujícím způsobem:  
  
```  
* [cv-qualifiers] identifier [= expression]  
```  
  
 1. Specifikátory deklarace:  
  
    - Volitelný specifikátor paměťové třídy. Další informace najdete v tématu [specifikátory](../cpp/specifiers.md).  
  
    - Volitelně **const** nebo **volatile** – klíčové slovo použití typu objekt, který má být odkazovala na.  
  
    - Specifikátor typu: název typu reprezentující typ objektu odkazovala na.  
  
 2. Deklarátor:  
  
    - Volitelný specifický modifikátor Microsoft. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
    - Operátor `*`.  
  
    - Volitelně **const** nebo **volatile** – klíčové slovo použití na ukazatel sám.  
  
    - Identifikátor.  
  
    - Volitelný inicializátor.  
  
     Deklarátoru ukazatele na funkce vypadá takto:  
  
```  
(* [cv-qualifiers] identifier )( argument-list ) [cv-qualifers]  
[exception specification] [= expression];  
```  
  
-   Pro pole ukazatelů syntaxe vypadá takto:  
  
```  
* identifier [ [ constant-expression ] ]  
```  
  
-   Jejich inicializátory a víc deklarátorů. může se zobrazí společně v jedné deklaraci v následující deklaraci specifikátor seznam oddělený čárkami.  
  
 Jednoduchý příklad deklaraci ukazatele je:  
  
```cpp 
char *pch;  
```  
  
 Předchozí deklarace Určuje, že `pch` odkazuje na objekt typu **char**.  
  
 Je složitější příklad  
  
```cpp 
static unsigned int * const ptr;  
```  
  
 Předchozí deklarace Určuje, že `ptr` konstantní ukazatel na objekt typu **bez znaménka** **int** s trváním statického úložiště.  
  
 Následující příklad ukazuje, jak více ukazatelů jsou deklarovány a inicializovány:  
  
```cpp 
static int *p = &i, *q = &j;  
```  
  
 V předchozím příkladu, přejděte na objekty typu ukazatele p a q **int** a jsou inicializovány na hodnotu adresy i a j v uvedeném pořadí.  Specifikátor třídy úložiště **statické** platí pro obě ukazatele.  
  
## <a name="example"></a>Příklad  
  
```cpp 
// pointer.cpp  
// compile with: /EHsc  
#include <iostream>  
int main() {  
   int i = 1, j = 2; // local variables on the stack  
   int *p;  
  
   // a pointer may be assigned to "point to" the value of  
   // another variable using the & (address of) operator  
   p = & j;   
  
   // since j was on the stack, this address will be somewhere  
   // on the stack.  Pointers are printed in hex format using  
   // %p and conventionally marked with 0x.    
   printf_s("0x%p\n",  p);  
  
   // The * (indirection operator) can be read as "the value  
   // pointed to by".  
   // Since p is pointing to j, this should print "2"  
   printf_s("0x%p %d\n",  p, *p);  
  
   // changing j will change the result of the indirection  
   // operator on p.  
   j = 7;  
   printf_s("0x%p %d\n",  p, *p );  
  
   // The value of j can also be changed through the pointer  
   // by making an assignment to the dereferenced pointer  
   *p = 10;  
   printf_s("j is %d\n", j); // j is now 10  
  
   // allocate memory on the heap for an integer,  
   // initialize to 5  
   p = new int(5);  
  
   // print the pointer and the object pointed to  
   // the address will be somewhere on the heap  
   printf_s("0x%p %d\n",  p, *p);  
  
   // free the memory pointed to by p  
   delete p;  
  
   // At this point, dereferencing p with *p would trigger  
   // a runtime access violation.  
  
   // Pointer arithmetic may be done with an array declared  
   // on the stack or allocated on the heap with new.  
   // The increment operator takes into account the size   
   // of the objects pointed to.  
   p = new int[5];  
   for (i = 0; i < 5; i++, p++) {  
      *p = i * 10;  
      printf_s("0x%p %d\n", p, *p);  
   }  
  
   // A common expression seen is dereferencing in combination  
   // with increment or decrement operators, as shown here.  
   // The indirection operator * takes precedence over the   
   // increment operator ++.   
   // These are particularly useful in manipulating char arrays.  
   char s1[4] = "cat";  
   char s2[4] = "dog";  
   char* p1 = s1;  
   char* p2 = s2;  
  
   // the following is a string copy operation  
   while (*p1++ = *p2++);  
  
   // s2 was copied into s1, so now they are both equal to "dog"  
   printf_s("%s %s", s1, s2);  
}  
```  
  
```Output  
0x0012FEC8  
0x0012FEC8 2  
0x0012FEC8 7  
j is 10  
0x00320850 5  
0x00320850 0  
0x00320854 10  
0x00320858 20  
0x0032085C 30  
0x00320860 40  
dog dog  
```  
  
## <a name="example"></a>Příklad  
 Další příklad ukazuje použití ukazatele ve strukturách dat; v tomto případě propojeného seznamu.  
  
```cpp 
// pointer_linkedlist.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct NewNode {  
   NewNode() : node(0){}  
   int i;  
   NewNode * node;  
};  
  
void WalkList(NewNode * ptr) {  
   if (ptr != 0) {  
      int i = 1;  
      while (ptr->node != 0 ) {  
         cout << "node " << i++ << " = " << ptr->i << endl;  
         ptr = ptr->node;  
      }  
      cout << "node " << i++ << " = " << ptr->i << endl;  
   }  
}  
  
void AddNode(NewNode ** ptr) {  
   NewNode * walker = 0;  
   NewNode * MyNewNode = new NewNode;  
   cout << "enter a number: " << endl;  
   cin >> MyNewNode->i;  
  
   if (*ptr == 0)  
      *ptr = MyNewNode;  
   else  {  
      walker = *ptr;  
      while (walker->node != 0)  
         walker = walker->node;  
  
      walker->node = MyNewNode;  
   }  
}  
  
int main() {  
   char ans = ' ';  
   NewNode * ptr = 0;  
   do {  
      cout << "a (add node)  d (display list)  q (quit)" << endl;  
      cin >> ans;  
      switch (ans) {  
      case 'a':  
         AddNode(&ptr);  
         break;  
      case 'd':  
         WalkList(ptr);  
         break;  
      }  
   } while (ans != 'q');  
}  
```  
  
```Output  
  
      a  
45  
d  
a  
789  
d  
qa (add node)  d (display list)  q (quit)  
enter a number:   
a (add node)  d (display list)  q (quit)  
node 1 = 45  
a (add node)  d (display list)  q (quit)  
enter a number:   
a (add node)  d (display list)  q (quit)  
node 1 = 45  
node 2 = 789  
a (add node)  d (display list)  q (quit)  
```  
  
## <a name="see-also"></a>Viz také  
 [Deferenční operátor: *](../cpp/indirection-operator-star.md)   
 [Operátor address-of: &](../cpp/address-of-operator-amp.md)