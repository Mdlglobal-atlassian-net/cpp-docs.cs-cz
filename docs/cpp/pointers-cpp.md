---
title: Ukazatele (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- declarators, pointers
- declarations, pointers
- pointers [C++]
- pointers, declarations
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a80b4227cd166edbbd146291ad57bd4efef95e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pointers-c"></a>Ukazatele (C++)
Ukazatele jsou deklarovány následujícím způsobem.  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator ;  
```  
  
 kde mohou být použity žádné platné ukazatel deklarátor pro `declarator`.  Syntaxe pro jednoduché ukazatel deklarátor vypadá takto:  
  
```  
* [cv-qualifiers] identifier [= expression]  
```  
  
 1. Specifikátory deklarace:  
  
-   Specifikátor třídy úložiště volitelné. Další informace najdete v tématu [specifikátory](../cpp/specifiers.md).  
  
-   Volitelný `const` nebo `volatile` použití typu objekt, který má být ukazuje – klíčové slovo.  
  
-   Specifikátor typu: název tohoto typu představující typ objektu, který chcete odkazovat.  
  
 2. Deklarátor:  
  
-   Volitelné Microsoft konkrétní modifikátor. Další informace najdete v tématu [Modifikátory specifické pro společnost Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
-   Operátor `*`.  
  
-   Volitelný `const` nebo `volatile` – klíčové slovo použití na samotný ukazatele.  
  
-   Identifikátor.  
  
-   Inicializátoru volitelné.  
  
 Deklarátor pro ukazatel na funkci, vypadá takto:  
  
```  
(* [cv-qualifiers] identifier )( argument-list ) [cv-qualifers]  
[exception specification] [= expression];  
```  
  
-   Pro pole ukazatele syntaxe vypadat třeba takto:  
  
```  
* identifier [ [ constant-expression ] ]  
```  
  
-   Více deklarátor a jejich inicializátory mohou objevit společně v jediné deklaraci v následujících Specifikátor deklarace seznam oddělený čárkami.  
  
 Jednoduchý příklad deklaraci ukazatel je:  
  
```  
char *pch;  
```  
  
 Předchozí deklaraci Určuje, že `pch` odkazuje na objekt typu `char`.  
  
 Ukázka je  
  
```  
static unsigned int * const ptr;  
```  
  
 Předchozí deklaraci Určuje, že `ptr` konstantní ukazatel na objekt typu `unsigned` `int` s úložiště se statickými doba trvání.  
  
 Další příklad ukazuje, jak více ukazatele deklarovat a inicializovat:  
  
```  
static int *p = &i, *q = &j;  
```  
  
 V předchozím příkladu, přejděte na objekty typu ukazatele p a q `int` a jsou inicializovány adresy i a j v uvedeném pořadí.  Specifikátor třídy úložiště `static` platí pro obě ukazatele.  
  
## <a name="example"></a>Příklad  
  
```  
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
 Další příklad ukazuje použití ukazatele v datové struktury; v tomto případě odkazovaného seznamu.  
  
```  
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
 [Adresa operátoru: &](../cpp/address-of-operator-amp.md)