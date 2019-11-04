---
title: pack – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 4bf0b3d4529de012f4a09d6e60a5b112b9a101df
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218763"
---
# <a name="pack-pragma"></a>pack – direktiva pragma

Určuje zarovnání balení pro členy struktury, sjednocení a třídy.

## <a name="syntax"></a>Syntaxe

> **#pragma pack( show )** \
> **#pragma pack ( push** [ **,** *Identifier* ] [ **,** *n* ] **)** \
> **#pragma pack ( pop** [ **;** { *identifikátor* | *n* }] **)** \
> **#pragma pack (** [ *n* ] **)**

### <a name="parameters"></a>Parametry

**show**\
Volitelné Zobrazí aktuální bajtovou hodnotu zarovnání balení. Hodnota se zobrazí ve zprávě upozornění.

**push**\
Volitelné Posune aktuální hodnotu zarovnání balení do vnitřního zásobníku kompilátoru a nastaví aktuální hodnotu zarovnání balení na *n*. Pokud není zadán *n* , aktuální hodnota zarovnání pro sbalení je vložena.

**pop**\
Volitelné Odebere záznam z horní části interního zásobníku kompilátoru. Pokud není zadán parametr *n* s příkazem **POP**, pak hodnota balení přidružená k výslednému záznamu v horní části zásobníku je nová hodnota zarovnání balení. Pokud je zadána hodnota *n* , například `#pragma pack(pop, 16)`,, *n* se bude novou hodnotou zarovnání balení. Pokud jste se přizpůsobili pomocí identifikátoru, `#pragma pack(pop, r1)`například, pak všechny záznamy v zásobníku budou odebrány, dokud nebude nalezen záznam s *identifikátorem* . Tento záznam se vyjímá a hodnota balení přidružená k výslednému záznamu v horní části zásobníku je nová hodnota zarovnání balení. Pokud jste přihlášeni pomocí identifikátoru, který nebyl nalezen v žádném záznamu v zásobníku, pak se **POP** ignoruje.

*RID*\
Volitelné Při použití s **nabízenou**sadou přiřadí název záznamu v interním zásobníku kompilátoru. Při použití s **POP**se odeberou záznamy z vnitřního zásobníku, dokud se neodebere *identifikátor* . Pokud *identifikátor* není v interním zásobníku nalezen, nic není vybráno.

*n*\
Volitelné Určuje hodnotu v bajtech, která se má použít k balení. Pokud pro modul není nastavená možnost kompilátoru [/zp](../build/reference/zp-struct-member-alignment.md) , výchozí hodnota pro *n* je 8. Platné hodnoty jsou 1, 2, 4, 8 a 16. Zarovnání člena je na hranici, která je buď násobkem *n*, nebo násobku velikosti členu, podle toho, která hodnota je menší.

`#pragma pack(pop, identifier, n)`není definováno.

## <a name="remarks"></a>Poznámky

Pro *sbalení* třídy je umístit členy přímo po sobě do paměti. Může to znamenat, že některé nebo všechny členy mohou být zarovnány na hranici menší než výchozí zarovnání cílové architektury. **sada** poskytuje řízení na úrovni deklarace dat. Liší se od možnosti kompilátoru [/zp](../build/reference/zp-struct-member-alignment.md), která poskytuje pouze ovládací prvek na úrovni modulu. **sada** se projeví při první **struktuře**, **sjednocení**nebo deklaraci **třídy** po vyřazení direktivy pragma. **sada** nemá žádný vliv na definice. Volání **Pack** bez argumentů nastaví *n* na hodnotu nastavenou v možnosti `/Zp`kompilátoru. Pokud není možnost kompilátoru nastavena, výchozí hodnota je 8.

Změníte-li zarovnání struktury, nemusí být využita tolik místa v paměti, ale může se stát, že dojde ke snížení výkonu, nebo dokonce získáte výjimku vygenerovanou hardwarem pro nezarovnaný přístup.  Toto chování výjimky můžete upravit pomocí [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode).

Další informace o tom, jak upravit zarovnání, najdete v těchto článcích:

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [Příklady zarovnání struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specifické pro procesory x64)

   > [!WARNING]
   > V aplikaci Visual Studio 2015 a novějších můžete použít standardní operátory **alignas** a **alignof** , které jsou na `__alignof` rozdíl `declspec( align )` od a přenosné mezi kompilátory. C++ Standard neřeší balení, takže je stále nutné použít **Pack** (nebo odpovídající rozšíření na jiných kompilátorech) k určení zarovnání menšího, než je velikost slova cílové architektury.

## <a name="examples"></a>Příklady

Následující příklad ukazuje, jak použít direktivu pragma **balíčku** pro změnu zarovnání struktury.

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

Následující příklad ukazuje, jak použít syntaxi *push*, *POP*a *show* .

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)