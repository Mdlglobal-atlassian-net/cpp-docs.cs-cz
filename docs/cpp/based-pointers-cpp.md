---
title: "Na základě ukazatele (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __based
- __based_cpp
dev_langs: C++
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b99696f125b0daf1cbd183a10ec9f741d525fa0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="based-pointers-c"></a>Základní ukazatelé (C++)
**Konkrétní Microsoft**  
  
 Klíčové slovo `__based` umožňuje deklarovat ukazatele založené na ukazatelích (ukazatele posunuté oproti existujícím ukazatelům).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
type __based( base ) declarator   
```  
  
## <a name="remarks"></a>Poznámky  
 Ukazatele založené na adresách ukazatelů jsou jedinou formou klíčového slova `__based`, která je platná ve 32bitových nebo 64bitových kompilacích. Pro 32bitové kompilátory jazyka C/C++ společnosti Microsoft je ukazatel základní třídy 32bitovým posunem oproti 32bitovému základu ukazatele. Podobné omezení platí pro 64bitová prostředí, kde je ukazatel základní třídy 64bitovým posunem oproti 64bitovému základu.  
  
 Jedním použitím ukazatelů na základě ukazatelů jsou trvalé identifikátory, které obsahují ukazatele. Propojený seznam, který se skládá z ukazatelů založených na ukazateli lze uložit na disk a následně jej lze znovu načíst na jiné místo v paměti, při současném zachování platnosti ukazatelů. Příklad:  
  
```  
// based_pointers1.cpp  
// compile with: /c  
void *vpBuffer;  
struct llist_t {  
   void __based( vpBuffer ) *vpData;  
   struct llist_t __based( vpBuffer ) *llNext;  
};  
```  
  
 Ukazateli `vpBuffer` je přiřazena adresa paměti, která je přidělena v programu později. Propojený seznam je přemístěn vzhledem k hodnotě `vpBuffer`.  
  
> [!NOTE]
>  Zachování identifikátory obsahující ukazatele provést taky pomocí [soubory mapované paměti](http://msdn.microsoft.com/library/windows/desktop/aa366556).  
  
 Při dereferenci ukazatele základní třídy musí být základ buď explicitně zadán, nebo implicitně znám prostřednictvím deklarace.  
  
 Pro kompatibilitu s předchozími verzemi **_based** se jedná o synonymum `__based`.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje změnu ukazatele základní třídy prostřednictvím změny jeho základu.  
  
```  
// based_pointers2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int a1[] = { 1,2,3 };  
int a2[] = { 10,11,12 };  
int *pBased;  
  
typedef int __based(pBased) * pBasedPtr;  
  
using namespace std;  
int main() {  
   pBased = &a1[0];  
   pBasedPtr pb = 0;  
  
   cout << *pb << endl;  
   cout << *(pb+1) << endl;  
  
   pBased = &a2[0];  
  
   cout << *pb << endl;  
   cout << *(pb+1) << endl;  
}  
```  
  
```Output  
1  
2  
10  
11  
```  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [alloc_text –](../preprocessor/alloc-text.md)