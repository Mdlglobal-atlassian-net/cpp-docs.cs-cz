---
title: Na základě ukazatele (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __based
- __based_cpp
dev_langs:
- C++
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afecaafc5a9d3c1eb9a9466cce303a493d355ce0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196204"
---
# <a name="based-pointers-c"></a>Základní ukazatelé (C++)
**Specifické pro Microsoft**  
  
 **__Based** – klíčové slovo umožňuje deklarovat ukazatele založené na ukazatelích (ukazatele posunuté oproti existujícím ukazatelům).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
type __based( base ) declarator   
```  
  
## <a name="remarks"></a>Poznámky  
 Ukazatele založené na adresách ukazatelů jsou jedinou formou **__based** – klíčové slovo v 32bitové nebo 64bitové kompilace platné. Pro 32bitové kompilátory jazyka C/C++ společnosti Microsoft je ukazatel základní třídy 32bitovým posunem oproti 32bitovému základu ukazatele. Podobné omezení platí pro 64bitová prostředí, kde je ukazatel základní třídy 64bitovým posunem oproti 64bitovému základu.  
  
 Jedním použitím ukazatelů na základě ukazatelů jsou trvalé identifikátory, které obsahují ukazatele. Propojený seznam, který se skládá z ukazatelů založených na ukazateli lze uložit na disk a následně jej lze znovu načíst na jiné místo v paměti, při současném zachování platnosti ukazatelů. Příklad:  
  
```cpp 
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
>  Zachování identifikátorů obsahujících ukazatele lze dosáhnout také pomocí [soubory mapované paměti](/windows/desktop/Memory/file-mapping).  
  
 Při dereferenci ukazatele základní třídy musí být základ buď explicitně zadán, nebo implicitně znám prostřednictvím deklarace.  
  
 Z důvodu kompatibility s předchozími verzemi **_založeno** je synonymum pro **__based**.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje změnu ukazatele základní třídy prostřednictvím změny jeho základu.  
  
```cpp 
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
  
## <a name="see-also"></a>Viz také:  
 [klíčová slova](../cpp/keywords-cpp.md)   
 [alloc_text](../preprocessor/alloc-text.md)