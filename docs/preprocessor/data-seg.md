---
title: data_seg | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
dev_langs:
- C++
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eed0e7616515d96c6ccba8cdcb56f963d13bf324
ms.sourcegitcommit: 80fc7b0452aafa36b0c915cbd29c75e1ffa25630
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003543"
---
# <a name="dataseg"></a>data_seg

Určuje datový segment inicializované proměnné, kde jsou uloženy v souboru .obj.

## <a name="syntax"></a>Syntaxe

```
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Parametry

**push**<br/>
(Volitelné) Vloží záznam do zásobníku vnitřního kompilátoru. A **nabízených** může mít *identifikátor* a *segment-name*.

**POP**<br/>
(Volitelné) Odstraní záznam z vrcholu vnitřního zásobníku kompilátoru.

*identifikátor*<br/>
(Volitelné) Při použití s **nabízených**, přiřadí název záznamu ve vnitřním zásobníku kompilátoru. Při použití s **pop**, vyjme všechny záznamy z vnitřního zásobníku až do *identifikátor* li *identifikátor* nebyl nalezen v interním zásobníku, nic nevezme.

*identifikátor* vyjmout několik záznamů lze jedním z jedné **pop** příkazu.

*"segment-name"*<br/>
(Volitelné) Název segmentu. Při použití s **pop**, je zásobník odebrán a *segment-name* stane aktivním názvem segmentu.

*"segmentu třídy"*<br/>
(Volitelné) Zahrnuto z důvodu kompatibility s jazykem C++ starším než verze 2.0. Ignorováno.

## <a name="remarks"></a>Poznámky

Významy pojmů *segmentu* a *části* jsou v tomto tématu zaměnitelné.

Soubory OBJ lze zobrazit pomocí [dumpbin](../build/reference/dumpbin-command-line.md) aplikace. .Data je výchozím segmentem v souboru .obj inicializované proměnných. Proměnné, které neinicializované jsou považovány za inicializovány na nulu a jsou uloženy v .bss.

**data_seg** bez parametrů obnoví nastavení segmentu na .data.

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

Data Alokovaná pomocí **data_seg** nezachovává žádné informace o jeho umístění.

Zobrazit [/SECTION](../build/reference/section-specify-section-attributes.md) seznam názvů byste neměli používat při tvorbě oddílu.

Můžete také určit oddíly pro proměnné const ([const_seg](../preprocessor/const-seg.md)), neinicializovaná data ([bss_seg](../preprocessor/bss-seg.md)) a funkce ([code_seg](../preprocessor/code-seg.md)).

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
