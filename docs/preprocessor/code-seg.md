---
title: code_seg – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: 65d702273593dc7fba68cc040f700b01a2c5e4a7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446465"
---
# <a name="code_seg-pragma"></a>code_seg – direktiva pragma

Určuje textový oddíl (segment), ve kterém jsou funkce uloženy v souboru objektu (. obj).

## <a name="syntax"></a>Syntaxe

> **#pragma code_seg (** ["*název oddílu*" [ **,** "*oddíl-Class*"]] **)** \
> **#pragma code_seg (** { **push** | **POP** } [ **,** *identifikátor* ] [ **,** "*oddílový název*" [ **,** "*oddíl-Class*"]] **)**

### <a name="parameters"></a>Parametry

\ **nabízených oznámení**
Volitelné Vloží záznam do interního zásobníku kompilátoru. **Nabízení oznámení** může mít *identifikátor* a *název oddílu*.

\ **POP**
Volitelné Odebere záznam z vrcholu vnitřního zásobníku kompilátoru. **POP** může mít *identifikátor* a *název oddílu*. Pomocí jednoho příkazu **POP** můžete v rámci *identifikátoru*otevřít více záznamů. Název *oddílu* se zobrazí jako název oddílu aktivního textu za bodem POP.

*identifikátor*\
Volitelné Při použití s **nabízenou**sadou přiřadí název záznamu v interním zásobníku kompilátoru. Při použití s **POP**direktiva vyřadí záznamy z vnitřního zásobníku, dokud se neodebere *identifikátor* . Pokud *identifikátor* není v interním zásobníku nalezen, nic není vybráno.

"*název oddílu*" \
Volitelné Název oddílu. Při použití s **bodem POP**se zásobník odstará a *název oddílu* se bude jmenovat jako aktivní textový oddíl.

"*oddíl-Class*" \
Volitelné Ignoruje se, ale je součástí kompatibility s verzemi C++ Microsoftu staršími než verze 2,0.

## <a name="remarks"></a>Poznámky

*Oddíl* v souboru objektu je pojmenovaný blok dat, který je načten do paměti jako jednotka. *Textový oddíl* je oddíl, který obsahuje spustitelný kód. V tomto článku mají *segment* a *oddíl* stejný význam.

Direktiva pragma **code_seg** instruuje kompilátor, aby každý následný objektový kód z jednotky překladu do textové části s názvem *section-name*. Ve výchozím nastavení je oddíl Text použitý pro funkce v souboru objektu pojmenován `.text`. Direktiva pragma **code_seg** bez parametru *název oddílu* obnoví název oddílu textu pro následný kód objektu na `.text`.

Direktiva pragma **code_seg** neřídí umístění kódu objektu generovaného pro instance šablon. Ani neřídí kód vygenerovaný implicitně kompilátorem, jako jsou například speciální členské funkce. Pro řízení tohoto kódu doporučujeme místo toho použít atribut [__declspec (code_seg (...))](../cpp/code-seg-declspec.md) . Poskytuje vám kontrolu nad umístěním veškerého kódu objektu, včetně kódu vygenerovaného kompilátorem.

Seznam názvů, které se nedají použít k vytvoření oddílu, najdete v tématu [/Section](../build/reference/section-specify-section-attributes.md).

Můžete také zadat oddíly pro inicializovaná data ([data_seg](../preprocessor/data-seg.md)), neinicializovaná data ([bss_seg](../preprocessor/bss-seg.md)) a proměnné const ([const_seg](../preprocessor/const-seg.md)).

Můžete použít [DUMPBIN. Aplikace EXE](../build/reference/dumpbin-command-line.md) pro zobrazení souborů objektů. Verze nástroje DUMPBIN pro každou podporovanou cílovou architekturu je součástí sady Visual Studio.

## <a name="example"></a>Příklad

Tento příklad ukazuje, jak použít direktivu pragma **code_seg** k určení, kam je kód objektu vložen:

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

## <a name="see-also"></a>Viz také

[code_seg (__declspec)](../cpp/code-seg-declspec.md)\
[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
