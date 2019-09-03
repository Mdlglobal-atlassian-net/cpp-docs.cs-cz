---
title: bss_seg – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: a343fb45b4bbe4789f38b7a1102572cf4241ec53
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218545"
---
# <a name="bss_seg-pragma"></a>bss_seg – direktiva pragma

Určuje oddíl (segment), kde jsou uloženy neinicializované proměnné v souboru objektu (. obj).

## <a name="syntax"></a>Syntaxe

> **#pragma bss_seg (** ["*název oddílu*" [ **,** "*oddíl-Class*"]] **)** \
> **#pragma bss_seg (** { **push** | **POP** } [ **,** *identifikátor* ] [ **,** "*oddíl-Name*" [ **;** "*Class-Class*"]] **)**

### <a name="parameters"></a>Parametry

**replik**\
Volitelné Vloží záznam do interního zásobníku kompilátoru. **Nabízení oznámení** může mít *identifikátor* a *název oddílu*.

**výstrah**\
Volitelné Odebere záznam z vrcholu vnitřního zásobníku kompilátoru. **POP** může mít *identifikátor* a *název oddílu*. Pomocí jednoho příkazu **POP** můžete v rámci identifikátoru otevřít více záznamů. Název *oddílu* se zobrazí jako aktivní název oddílu BSS za bodem POP.

*RID*\
Volitelné Při použití s **nabízenou**sadou přiřadí název záznamu v interním zásobníku kompilátoru. Při použití s **POP**direktiva vyřadí záznamy z vnitřního zásobníku, dokud se neodebere *identifikátor* . Pokud *identifikátor* není v interním zásobníku nalezen, nic není vybráno.

*"název oddílu"* \
Volitelné Název oddílu. Při použití s **bodem POP**se zásobník vyjímá a *název oddílu* se zobrazí jako aktivní název oddílu BSS.

*"oddíl-Class"* \
Volitelné Ignoruje se, ale je součástí kompatibility s verzemi C++ Microsoftu staršími než verze 2,0.

## <a name="remarks"></a>Poznámky

*Oddíl* v souboru objektu je pojmenovaný blok dat, který je načten do paměti jako jednotka. *Oddíl BSS* je oddíl, který obsahuje neinicializovaná data. V tomto článku mají *segment* a *oddíl* stejný význam.

Direktiva pragma **bss_seg** instruuje kompilátor, aby uvedl všechny neinicializované datové položky z jednotky překladu do oddílu BSS s názvem *section-name*. V některých případech může použití **bss_seg** zrychlit načítání tím, že seskupí neinicializovaná data do jednoho oddílu. Ve výchozím nastavení se název oddílu BSS, který se používá pro neinicializovaná data v souboru objektu `.bss`, nazývá. Direktiva pragma **bss_seg** bez parametru *section-name* obnoví název oddílu BSS pro následné neinicializované položky dat na `.bss`.

Data přidělená pomocí direktivy pragma **bss_seg** neuchovávají žádné informace o umístění.

Seznam názvů, které se nedají použít k vytvoření oddílu, najdete v tématu [/Section](../build/reference/section-specify-section-attributes.md).

Můžete také zadat oddíly pro inicializovaná data ([data_seg](../preprocessor/data-seg.md)), Functions ([code_seg](../preprocessor/code-seg.md)) a const Variables ([const_seg](../preprocessor/const-seg.md)).

Můžete použít [DUMPBIN. Aplikace EXE](../build/reference/dumpbin-command-line.md) pro zobrazení souborů objektů. Verze nástroje DUMPBIN pro každou podporovanou cílovou architekturu je součástí sady Visual Studio.

## <a name="example"></a>Příklad

```cpp
// pragma_directive_bss_seg.cpp
int i;                     // stored in .bss
#pragma bss_seg(".my_data1")
int j;                     // stored in .my_data1

#pragma bss_seg(push, stack1, ".my_data2")
int l;                     // stored in .my_data2

#pragma bss_seg(pop, stack1)   // pop stack1 from stack
int m;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
