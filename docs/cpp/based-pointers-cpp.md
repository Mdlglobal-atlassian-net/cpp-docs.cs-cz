---
title: Základní ukazatelé (C++)
ms.date: 10/09/2018
f1_keywords:
- __based
- _based
- __based_cpp
helpviewer_keywords:
- __based keyword [C++]
- based pointers
- pointers, based
ms.assetid: 1e5f2e96-c52e-4738-8e14-87278681205e
ms.openlocfilehash: 24c3a7f85c4ea05c38f3ab1d3f637ea0ab24d4c5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363745"
---
# <a name="based-pointers-c"></a>Základní ukazatelé (C++)

Klíčové slovo **__based** umožňuje deklarovat ukazatele na základě ukazatelů (ukazatele, které jsou posuny od existujícíukazatele). Klíčové slovo **__based** je specifické pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

```
type __based( base ) declarator
```

## <a name="remarks"></a>Poznámky

Ukazatele založené na adresách ukazatele jsou jedinou formou **klíčového** slova __based platného v 32bitových nebo 64bitových kompilacích. Pro 32bitové kompilátory jazyka C/C++ společnosti Microsoft je ukazatel základní třídy 32bitovým posunem oproti 32bitovému základu ukazatele. Podobné omezení platí pro 64bitová prostředí, kde je ukazatel základní třídy 64bitovým posunem oproti 64bitovému základu.

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
> Trvalé identifikátory obsahující ukazatele lze také provést pomocí [souborů mapovaných v paměti](/windows/win32/Memory/file-mapping).

Při dereferenci ukazatele základní třídy musí být základ buď explicitně zadán, nebo implicitně znám prostřednictvím deklarace.

Pro kompatibilitu s předchozími verzemi **je _based** synonymem pro **__based** pokud není zadána možnost kompilátoru [/Za \(Zakázat rozšíření jazyka).](../build/reference/za-ze-disable-language-extensions.md)

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

## <a name="see-also"></a>Viz také

[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[alloc_text](../preprocessor/alloc-text.md)
