---
title: Identifikátory prostředků (symboly) (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.identifiers
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
ms.openlocfilehash: c6b3cf7d3edfc870164645632bb07bf49c792a48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359891"
---
# <a name="resource-identifiers-symbols-c"></a>Identifikátory prostředků (symboly) (C++)

Symbol je identifikátor prostředku (ID), který se skládá ze dvou částí, název symbolu (textový řetězec) mapovaný na hodnotu symbolu (celé číslo), například:

```cpp
IDC_EDITNAME = 5100
```

Názvy symbolů se nejčastěji označují jako identifikátory.

Symboly poskytují popisný způsob odkazování na prostředky a objekty uživatelského rozhraní, a to jak ve zdrojovém kódu, tak při práci s nimi v editorech prostředků. Symboly můžete zobrazit a manipulovat s nimi na jednom vhodném místě pomocí [dialogového okna Symboly prostředků](../windows/viewing-resource-symbols.md).

Jak vaše aplikace roste ve velikosti a propracovanosti, tak se jeho počet prostředků a symbolů. Sledování velkého počtu symbolů rozptýlených v několika souborech může být obtížné. Dialogové okno **Symboly prostředků** zjednodušuje správu symbolů tím, že nabízí centrální nástroj, jehož prostřednictvím můžete:

- [Vytvořit symboly](../windows/creating-new-symbols.md)

- [Správa symbolů](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Zobrazit předdefinovaná ID symbolů](../windows/predefined-symbol-ids.md)

Při vytváření nového objektu prostředku nebo prostředku poskytují [editory prostředků](../windows/resource-editors.md) výchozí `IDC_RADIO1`název prostředku, například , a přiřazují mu hodnotu. Definice názvu plus hodnoty je uložena v souboru. `Resource.h`

> [!NOTE]
> Při kopírování prostředků nebo objektů prostředků z jednoho souboru RC do jiného může visual c++ změnit hodnotu symbolu přenesené ho prostředku nebo název a hodnotu symbolu, aby se zabránilo konfliktům s názvy symbolů nebo hodnotami v existujícím souboru.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>
