---
title: Pack | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- pack_CPP
- vc-pragma.pack
dev_langs:
- C++
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c29c31cae2b7de59d4db5ed6546ad4eda6baecf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="pack"></a>pack
Určuje zarovnání okolních struktury, sjednocení a členy třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )  
```  
  
## <a name="remarks"></a>Poznámky  
 Pack třídu je přímo po navzájem v paměti, což může znamenat, že některé nebo všechny členy lze zarovnávat na hranici menší než výchozí zarovnání architekturu cílového umístit její členy. `pack` nabízí řízení na úrovni dat deklarace. Tím se liší od – možnost kompilátoru [/Zp](../build/reference/zp-struct-member-alignment.md), který poskytuje jenom úroveň modulu řízení. `pack` v první se projeví `struct`, `union`, nebo `class` deklarace po je vidět – Direktiva pragma. `pack` nemá žádný vliv na definice. Volání metody `pack` s žádné argumenty sady `n` je hodnota nastavená v kompilátoru možnosti **/Zp**. Pokud není nastavena možnost kompilátoru, výchozí hodnota je 8.  
  
 Pokud změníte zarovnání struktury, se nemusí používat jako, kolik místa v paměti, ale může najdete v části ke snížení výkonu nebo i požádat o výjimku generované hardwaru pro nezarovnané přístup.  Toto chování výjimka můžete upravit pomocí [SetErrorMode](http://msdn.microsoft.com/library/windows/desktop/ms680621).  
  
 **Zobrazit** (volitelné)  
 Zobrazí aktuální hodnotu bajtu pro balení zarovnání. Ve upozornění se zobrazí hodnota.  
  
 **nabízená** (volitelné)  
 Hodnota aktuální zarovnání okolních se nabízených oznámení v zásobníku vnitřní kompilátoru a nastaví hodnotu aktuální zarovnání okolních `n`. Pokud `n` není zadán, aktuální balení zarovnání hodnota se instaluje.  
  
 **POP** (volitelné)  
 Odebere položku z horní části zásobníku vnitřní kompilátoru. Pokud `n` není zadaný s **pop**, je hodnota okolních přidružená výsledný záznam v horní části zásobníku nové balení zarovnání hodnotu. Pokud `n` není zadaný, například `#pragma pack(pop, 16)`, `n` stane nový balení zarovnání hodnotu. Pokud pop s `identifier`, například `#pragma pack(pop, r1)`, pak všechny záznamy v zásobníku jsou odebrány až záznam, který má `identifier` nalezen. Že záznamu je odebrány a okolních hodnotu přidruženou výsledný záznam na zásobníku nové okolních zarovnání hodnotu. Pokud pop s `identifier` který se nenachází v žádné záznamu v zásobníku, pak se **pop** je ignorována.  
  
 `identifier` (volitelné)  
 Při použití s **nabízené**, přiřadí název záznamu v zásobníku vnitřní kompilátoru. Při použití s **pop**, POP záznamy ze zásobníku vnitřní, dokud `identifier` odebrána; Pokud `identifier` nebyl nalezen v interní zásobníku, nic se odebrány.  
  
 `n` (volitelné)  
 Určuje hodnotu, v bajtech, který se má použít pro okolních. Pokud – možnost kompilátoru [/Zp](../build/reference/zp-struct-member-alignment.md) není nastaven pro modul, výchozí hodnota pro `n` je 8. Platné hodnoty jsou 1, 2, 4, 8 a 16. Zarovnání člen bude na hranici, která je buď násobkem `n` nebo násobek velikosti člena, podle toho, která je menší.  
  
 `#pragma pack(pop, identifier, n)` není definován.  
  
 Další informace o tom, jak upravit zarovnání, najdete v těchto tématech:  
  
-   [__alignof](../cpp/alignof-operator.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md) (x64 konkrétní)  
  
    > [!WARNING]
    >  Všimněte si, že v sadě Visual Studio 2015 a novější můžete použít operátory alignof a alignas standardní který, na rozdíl od `__alignof` a `declspec( align )` jsou přenosné napříč kompilátory. Standardní C++ neřeší balení, takže je nutné použít `pack` (nebo odpovídající rozšíření na jiné kompilátory) k určení zarovnání menší než velikost cílové architektury aplikace word.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `pack` – Direktiva pragma, chcete-li změnit zarovnání struktury.  
  
```  
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
  
```  
0 4 8  
0 4 6  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití **nabízené**, **pop**, a **zobrazit** syntaxe.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)