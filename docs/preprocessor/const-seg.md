---
title: const_seg – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
ms.openlocfilehash: 845583889eb922ba97d145eefe6bca280a83817b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220429"
---
# <a name="const_seg-pragma"></a>const_seg – direktiva pragma

Určuje oddíl (segment), kde jsou uloženy [konstantní](../cpp/const-cpp.md) proměnné v souboru objektu (. obj).

## <a name="syntax"></a>Syntaxe

> **#pragma const_seg (** ["*název oddílu*" [ **,** "*oddíl-Class*"]] **)** \
> **#pragma const_seg (** { **push** | **POP** } [ **,** *identifikátor* ] [ **,** "*oddíl-Name*" [ **;** "*Class-Class*"]] **)**

### <a name="parameters"></a>Parametry

**replik**\
Volitelné Vloží záznam do interního zásobníku kompilátoru. **Nabízení oznámení** může mít *identifikátor* a *název oddílu*.

**výstrah**\
Volitelné Odebere záznam z vrcholu vnitřního zásobníku kompilátoru. **POP** může mít *identifikátor* a *název oddílu*. Pomocí jednoho příkazu **POP** můžete v rámci identifikátoru otevřít více záznamů. Název *oddílu* se po zobrazení pop zobrazí jako aktivní název oddílu const.

*RID*\
Volitelné Při použití s **nabízenou**sadou přiřadí název záznamu v interním zásobníku kompilátoru. Při použití s **POP**direktiva vyřadí záznamy z vnitřního zásobníku, dokud se neodebere *identifikátor* . Pokud *identifikátor* není v interním zásobníku nalezen, nic není vybráno.

"*název oddílu*" \
Volitelné Název oddílu. Při použití s **bodem POP**se zásobník odstará a *název oddílu* se zobrazí jako aktivní název oddílu const.

"*oddíl-Class*" \
Volitelné Ignoruje se, ale je součástí kompatibility s verzemi C++ Microsoftu staršími než verze 2,0.

## <a name="remarks"></a>Poznámky

*Oddíl* v souboru objektu je pojmenovaný blok dat, který je načten do paměti jako jednotka. *Oddíl const* je oddíl, který obsahuje konstantní data. V tomto článku mají *segment* a *oddíl* stejný význam.

Direktiva pragma **const_seg** instruuje kompilátor, aby všechny konstantní datové položky z jednotky překladu do oddílu const s názvem *section-name*. Výchozí oddíl v souboru objektu pro proměnné const je. `.rdata` Některé proměnné const, například skalární, jsou automaticky vloženy do datového proudu kódu. Vložená kód se nezobrazuje v `.rdata`. Direktiva pragma **const_seg** bez parametru *názvu oddílu* obnoví název oddílu pro následné **konstantní** datové položky na `.rdata`.

Definujete-li objekt, který vyžaduje dynamickou inicializaci `const_seg`v, je výsledkem nedefinované chování.

Seznam názvů, které se nedají použít k vytvoření oddílu, najdete v tématu [/Section](../build/reference/section-specify-section-attributes.md).

Můžete také zadat oddíly pro inicializovaná data ([data_seg](../preprocessor/data-seg.md)), neinicializovaná data ([bss_seg](../preprocessor/bss-seg.md)) a funkce ([code_seg](../preprocessor/code-seg.md)).

Můžete použít [DUMPBIN. Aplikace EXE](../build/reference/dumpbin-command-line.md) pro zobrazení souborů objektů. Verze nástroje DUMPBIN pro každou podporovanou cílovou architekturu je součástí sady Visual Studio.

## <a name="example"></a>Příklad

```cpp
// pragma_directive_const_seg.cpp
// compile with: /EHsc
#include <iostream>

const int i = 7;               // inlined, not stored in .rdata
const char sz1[]= "test1";     // stored in .rdata

#pragma const_seg(".my_data1")
const char sz2[]= "test2";     // stored in .my_data1

#pragma const_seg(push, stack1, ".my_data2")
const char sz3[]= "test3";     // stored in .my_data2

#pragma const_seg(pop, stack1) // pop stack1 from stack
const char sz4[]= "test4";     // stored in .my_data1

int main() {
    using namespace std;
   // const data must be referenced to be put in .obj
   cout << sz1 << endl;
   cout << sz2 << endl;
   cout << sz3 << endl;
   cout << sz4 << endl;
}
```

```Output
test1
test2
test3
test4
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
