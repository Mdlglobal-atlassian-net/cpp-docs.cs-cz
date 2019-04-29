---
title: code_seg
ms.date: 11/04/2016
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: e566fb01bf70b343b75254a10466bdda2bc7ce1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403500"
---
# <a name="codeseg"></a>code_seg
Určuje textový segment, kde jsou funkce uloženy v souboru .obj.

## <a name="syntax"></a>Syntaxe

```
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Parametry

**push**<br/>
(Volitelné) Vloží záznam do zásobníku vnitřního kompilátoru. A **nabízených** může mít *identifikátor* a *segment-name*.

**pop**<br/>
(Volitelné) Odstraní záznam z vrcholu vnitřního zásobníku kompilátoru.

*identifier*<br/>
(Volitelné) Při použití s **nabízených**, přiřadí název záznamu ve vnitřním zásobníku kompilátoru. Při použití s **pop**, vyjme všechny záznamy z vnitřního zásobníku až do *identifikátor* li *identifikátor* nebyl nalezen v interním zásobníku, nic nevezme.

*identifikátor* vyjmout několik záznamů pro odebrání pouze s jedním **pop** příkazu.

"*segment-name*"<br/>
(Volitelné) Název segmentu. Při použití s **pop**, je zásobník odebrán a *segment-name* stane názvem textového segmentu.

"*segment-class*"<br/>
(Volitelné) Ignorováno, ale zahrnuto pro kompatibilitu s verzemi jazyka C++ před verzí 2.0.

## <a name="remarks"></a>Poznámky

**Code_seg** – Direktiva pragma neřídí umístění objektového kódu generovaného pro instancované šablony ani kódu generovaného implicitně kompilátorem, například zvláštní členské funkce. Doporučujeme použít [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) místo toho atribut, protože s ním můžete ovládat umístění celého objektového kódu. To zahrnuje kód generovaný kompilátorem.

A *segmentu* soubor v .obj je pojmenovaný blok dat, který je načten do paměti jako celek. A *textový segment* je segment, který obsahuje spustitelný kód. V tomto článku se podmínky *segmentu* a *části* zaměňují.

**Code_seg** – Direktiva pragma instruuje kompilátor, aby uvedl veškerý následný objektový kód z převodu jednotky do textového segmentu text s názvem *segment-name*. Ve výchozím nastavení se textový segment použitý v souboru .obj nazývá .text.

A **code_seg** – Direktiva pragma bez parametrů obnoví název textového segmentu pro následný objektový kód na .text.

Můžete použít [DUMPBIN. Soubor EXE](../build/reference/dumpbin-command-line.md) aplikace k zobrazení souborů obj. Součástí sady Visual Studio jsou verze DUMPBIN pro každou podporovanou cílovou architekturu.

## <a name="example"></a>Příklad

Tento příklad ukazuje způsob použití **code_seg** – Direktiva pragma pro ovládací prvek, kde objektového kódu:

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

Seznam názvů, které by neměly být použít k vytvoření oddílu, naleznete v tématu [/SECTION](../build/reference/section-specify-section-attributes.md).

Můžete také určit oddíly pro inicializovaná data ([data_seg](../preprocessor/data-seg.md)), neinicializovaná data ([bss_seg](../preprocessor/bss-seg.md)) a proměnné const ([const_seg](../preprocessor/const-seg.md)).

## <a name="see-also"></a>Viz také:

[code_seg (__declspec)](../cpp/code-seg-declspec.md)<br/>
[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)