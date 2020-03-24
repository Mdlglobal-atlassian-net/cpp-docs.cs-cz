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
ms.openlocfilehash: f16e9f6582ae846c0c19fc1dcbd86f09baba713e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181392"
---
# <a name="based-pointers-c"></a>Základní ukazatelé (C++)

Klíčové slovo **__based** umožňuje deklaraci ukazatelů na základě ukazatelů (ukazatelů, které jsou posunuty od stávajících ukazatelů). Klíčové slovo **__based** je specifické pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

```
type __based( base ) declarator
```

## <a name="remarks"></a>Poznámky

Ukazatele založené na adresách ukazatelů jsou jedinou formou klíčového slova **__based** platné v 32 bitových nebo 64 bitových kompilacích. Pro 32bitové kompilátory jazyka C/C++ společnosti Microsoft je ukazatel základní třídy 32bitovým posunem oproti 32bitovému základu ukazatele. Podobné omezení platí pro 64bitová prostředí, kde je ukazatel základní třídy 64bitovým posunem oproti 64bitovému základu.

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
>  Trvalé identifikátory s ukazateli lze také provést pomocí [souborů mapovaných do paměti](/windows/win32/Memory/file-mapping).

Při dereferenci ukazatele základní třídy musí být základ buď explicitně zadán, nebo implicitně znám prostřednictvím deklarace.

Z důvodu kompatibility s předchozími verzemi je **_based** synonymem pro **__based** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

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
