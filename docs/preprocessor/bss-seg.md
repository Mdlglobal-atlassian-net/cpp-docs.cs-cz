---
title: bss_seg | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77d234acdc02a2fefeca45ca0a925603e0ff9984
ms.sourcegitcommit: 80fc7b0452aafa36b0c915cbd29c75e1ffa25630
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003556"
---
# <a name="bssseg"></a>bss_seg

Určuje segment neinicializované proměnné, kde jsou uloženy v souboru .obj.

## <a name="syntax"></a>Syntaxe

```
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Parametry

**push**<br/>
(Volitelné) Vloží záznam do zásobníku vnitřního kompilátoru. A *pu*TV * může mít *identifikátor* a *segment-name*.

**POP**<br/>
(Volitelné) Odstraní záznam z vrcholu vnitřního zásobníku kompilátoru.

*identifikátor*<br/>
(Volitelné) Při použití s **nabízených**, přiřadí název záznamu ve vnitřním zásobníku kompilátoru. *identifikátor* vyjmout několik záznamů lze jedním z jedné **pop** příkazu. Při použití s **pop**, direktivy Vyjme všechny záznamy z vnitřního zásobníku až do *identifikátor* li *identifikátor* nebyl nalezen v interním zásobníku, nic není odebrány.

*"segment-name"*<br/>
(Volitelné) Název segmentu. Při použití s **pop**, je zásobník odebrán a *segment-name* stane aktivním názvem segmentu.

*"segmentu třídy"*<br/>
(Volitelné) Zahrnuto z důvodu kompatibility s jazykem C++ starším než verze 2.0. Ignorováno.

## <a name="remarks"></a>Poznámky

. Soubory obj lze zobrazit pomocí [dumpbin](../build/reference/dumpbin-command-line.md) aplikace. Výchozí segment v souboru obj neinicializovaná data je .bss. V některých případech použití **bss_seg** můžete urychlit načítání časy seskupením neinicializovaná data do jednoho oddílu.

**bss_seg** bez parametrů obnoví nastavení segmentu na .bss.

Data Alokovaná pomocí **bss_seg** – Direktiva pragma nezachovává žádné informace o jeho umístění.

Můžete také určit oddíly pro inicializovaná data ([data_seg](../preprocessor/data-seg.md)), funkce ([code_seg](../preprocessor/code-seg.md)) a proměnné const ([const_seg](../preprocessor/const-seg.md)).

Zobrazit [/SECTION](../build/reference/section-specify-section-attributes.md) seznam názvů byste neměli používat při tvorbě oddílu.

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

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
