---
title: "C3066 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3066
dev_langs: C++
helpviewer_keywords: C3066
ms.assetid: 226f6de5-c4c5-41e2-b31a-2e30a37fbbeb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e131d44a3a5ffbab2874f8e524d0f57ddc77faa2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3066"></a>C3066 chyby kompilátoru
existuje více způsobů, že objekt tohoto typu lze volat s těmito argumenty  
  
 Kompilátor zjištěna volání funkce nejednoznačný zahrnující náhrady.  
  
 Následující ukázka generuje C3066:  
  
```  
// C3066.cpp  
template <class T, class U> void func(T*, U*){}  
  
typedef void (*PF)(const int*, const char*);  
typedef void (*PF1)(const int*, volatile char*);  
  
struct A {  
   operator PF() const {  
      return func;  
   }  
  
   operator PF1() {  
      return func;  
   }  
  
   operator PF1() const  {  
      return func;  
   }  
  
};  
  
int main() {  
   A a;  
   int i;  
   char c;  
  
   a(&i, &c);   // C3066  
   a(&i, (const char *) &c);   // OK  
}  
```

## <a name="copy-list-initialization"></a>Kopie – seznam – inicializace
V sadě Visual Studio 2015 kompilátor chybnou informací považovat kopírování. seznam inicializace stejným způsobem jako regulární kopie inicializace; považuje za pouze převod konstruktory pro rozlišení přetížení. V následujícím příkladu Visual Studio 2015 zvolí MyInt(23) ale Visual Studio 2017 správně vyvolá chybu.

```
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyList {
       explicit MyStore(int initialCapacity);
};

struct MyInt {
       MyInt(int i);
};

struct Printer {
       void operator()(MyStore const& s);
       void operator()(MyInt const& i);
};

void f() {
       Printer p;
       p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```