---
title: data_seg – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: f67a9f39695adf5067c61288cf09ea7eb481c7dd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220377"
---
# <a name="data_seg-pragma"></a>data_seg – direktiva pragma

Určuje oddíl dat (segment), kde jsou uloženy inicializované proměnné v souboru objektu (. obj).

## <a name="syntax"></a>Syntaxe

> **#pragma data_seg (** ["*název oddílu*" [ **,** "*oddíl-Class*"]] **)** \
> **#pragma data_seg (** { **push** | **POP** } [ **,** *identifikátor* ] [ **,** "*oddíl-Name*" [ **;** "*Class-Class*"]] **)**

### <a name="parameters"></a>Parametry

**replik**\
Volitelné Vloží záznam do interního zásobníku kompilátoru. **Nabízení oznámení** může mít *identifikátor* a *název oddílu*.

**výstrah**\
Volitelné Odebere záznam z vrcholu vnitřního zásobníku kompilátoru. **POP** může mít *identifikátor* a *název oddílu*. Pomocí jednoho příkazu **POP** můžete v rámci identifikátoru otevřít více záznamů. Název *oddílu* se po zobrazení pop stal názvem oddílu aktivní data.

*RID*\
Volitelné Při použití s **nabízenou**sadou přiřadí název záznamu v interním zásobníku kompilátoru. Při použití s **POP**se odeberou záznamy z vnitřního zásobníku, dokud se neodebere *identifikátor* . Pokud *identifikátor* není v interním zásobníku nalezen, nic není vybráno.

*identifikátor* umožňuje odebrání více záznamů jediným příkazem **POP** .

*"název oddílu"* \
Volitelné Název oddílu. Při použití s **bodem POP**se zásobník odstará a *název oddílu* se stal názvem oddílu aktivní data.

*"oddíl-Class"* \
Volitelné Ignoruje se, ale je součástí kompatibility s verzemi C++ Microsoftu staršími než verze 2,0.

## <a name="remarks"></a>Poznámky

*Oddíl* v souboru objektu je pojmenovaný blok dat, který je načten do paměti jako jednotka. *Oddíl dat* je oddíl, který obsahuje inicializovaná data. V tomto článku mají *segment* a *oddíl* stejný význam.

Výchozí oddíl v souboru. obj pro inicializované proměnné je `.data`. Proměnné, které jsou neinicializované, jsou považovány za inicializované na nulu a jsou uloženy `.bss`v.

Direktiva pragma **data_seg** instruuje kompilátor, aby uvedl všechny inicializované datové položky z jednotky překladu do datové části s názvem *section-name*. Ve výchozím nastavení se `.data`používá oddíl dat pro inicializovaná data v souboru objektu. Proměnné, které jsou neinicializované, jsou považovány za inicializované na nulu a jsou uloženy v `.bss`. Direktiva pragma **data_seg** bez parametru *section-name* obnoví název oddílu dat pro následné položky inicializovaných dat na `.data`.

Data přidělená pomocí **data_seg** neuchovávají žádné informace o jeho umístění.

Seznam názvů, které se nedají použít k vytvoření oddílu, najdete v tématu [/Section](../build/reference/section-specify-section-attributes.md).

Můžete také zadat oddíly pro const Variables ([const_seg](../preprocessor/const-seg.md)), neinicializovaná data ([bss_seg](../preprocessor/bss-seg.md)) a Functions ([code_seg](../preprocessor/code-seg.md)).

Můžete použít [DUMPBIN. Aplikace EXE](../build/reference/dumpbin-command-line.md) pro zobrazení souborů objektů. Verze nástroje DUMPBIN pro každou podporovanou cílovou architekturu je součástí sady Visual Studio.

## <a name="example"></a>Příklad

```cpp
// pragma_directive_data_seg.cpp
int h = 1;                     // stored in .data
int i = 0;                     // stored in .bss
#pragma data_seg(".my_data1")
int j = 1;                     // stored in .my_data1

#pragma data_seg(push, stack1, ".my_data2")
int l = 2;                     // stored in .my_data2

#pragma data_seg(pop, stack1)   // pop stack1 off the stack
int m = 3;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
