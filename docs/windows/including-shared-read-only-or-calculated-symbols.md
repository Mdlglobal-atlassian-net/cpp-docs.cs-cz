---
title: Zahrnutí sdílených (jen pro čtení) nebo vypočtených symbolů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.shared.calculated
dev_langs:
- C++
helpviewer_keywords:
- symbols, read-only
- symbols, shared
- symbols, calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 29449031485f1b701d6b6a1cfe671993c5ebc73a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589312"
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>Zahrnutí sdílených (jen pro čtení) nebo vypočtených symbolů

Při prvním vývojové prostředí přečte soubor prostředků vytvořený v jiné aplikaci, označí všechny soubory zahrnuté záhlaví jen pro čtení. Následně můžete použít [dialogové okno prostředek zahrnuje](../windows/resource-includes-dialog-box.md) přidat soubory hlaviček další symbolů jen pro čtení.

Jedním z důvodů, že můžete chtít použít definice symbolů jen pro čtení se pro soubory symbolů, které máte v plánu sdílet mezi více projekty.

Soubory zahrnuté symbolů můžete použít také v případě, že máte existující prostředky s definice symbolů, které definovat hodnotu symbolu pomocí výrazů spíše než jednoduché celých čísel. Příklad:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```

Prostředí se správně interpretovat tyto počítané symboly, pokud:

- Počítané symboly jsou umístěny v souboru symbolů jen pro čtení.

- Soubor prostředků obsahuje prostředky, ke kterým jsou už přiřazené tyto počítané symboly.

- Je očekáván číselný výraz.

> [!NOTE]
> Pokud se očekává řetězec nebo číselný výraz, výraz není vyhodnocen.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Zahrnout do souboru prostředků sdílené symboly (pouze pro čtení)

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a zvolte [prostředek zahrnuje](../windows/resource-includes-dialog-box.md) z místní nabídky.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V **měrnice souborů jen pro čtení** pole, použijte `#include` direktivy kompilátoru k určení souboru, kam chcete uchovávat symbolů jen pro čtení.

   Nevolejte soubor `Resource.h`, protože se běžně používá hlavičkový soubor symbolů hlavní název souboru.

   > [!NOTE]
   > **Důležité** zadejte v poli direktivy symbolů jen pro čtení je součástí souboru prostředků přesně během psaní. Ujistěte se, jaký typ neobsahuje chyby syntaxe nebo kontrolu pravopisu.

   Použití **měrnice souborů jen pro čtení** pole mají zahrnout soubory s pouze definice symbolů. Nezahrnují definice prostředků. v opačném případě duplicitní prostředek, který definice se vytvoří, když je soubor uložen.

3. Umístění symbolů v souboru, který jste zadali.

   Symboly v souborech tímto způsobem jsou vyhodnocovány pokaždé, když otevřete soubor prostředků, ale nejsou při uložení souboru nahrazena na disku.

4. Klikněte na tlačítko **OK**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Omezení názvu symbolu](../windows/symbol-name-restrictions.md)  
[Omezení hodnoty symbolu](../windows/symbol-value-restrictions.md)  
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)  
[Symboly: Identifikátory prostředků](../windows/symbols-resource-identifiers.md)