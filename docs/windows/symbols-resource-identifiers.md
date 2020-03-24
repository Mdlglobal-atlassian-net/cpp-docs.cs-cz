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
ms.openlocfilehash: ba0958e455557660ef704f1c2fa570d46307082f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214393"
---
# <a name="resource-identifiers-symbols-c"></a>Identifikátory prostředků (symboly) (C++)

Symbol je identifikátor prostředku (ID), který se skládá ze dvou částí, název symbolu (textový řetězec) mapovaný na hodnotu symbolu (celé číslo), například:

```
IDC_EDITNAME = 5100
```

Názvy symbolů se nejčastěji označují jako identifikátory.

Symboly poskytují popisný způsob, jak odkazovat na prostředky a objekty uživatelského rozhraní, jak ve zdrojovém kódu, tak i když s nimi pracujete v editorech prostředků. Symboly můžete zobrazit a manipulovat na jednom místě pomocí [dialogového okna symboly prostředků](../windows/viewing-resource-symbols.md).

Vzhledem k tomu, že se vaše aplikace zvětšuje a sofistikovanější, tak je jejich počet zdrojů a symbolů. Sledování velkého počtu symbolů rozptýlených v několika souborech může být obtížné. Dialogové okno **symboly prostředků** zjednodušuje správu symbolů tím, že nabízí centrální nástroj, pomocí kterého můžete:

- [Vytváření symbolů](../windows/creating-new-symbols.md)

- [Správa symbolů](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Zobrazit předdefinovaná ID symbolů](../windows/predefined-symbol-ids.md)

Při vytváření nového objektu prostředku nebo prostředku poskytují [editory prostředků](../windows/resource-editors.md) výchozí název prostředku, například `IDC_RADIO1`a přiřadí mu hodnotu. Definice název a hodnota je uložená v souboru `Resource.h`.

> [!NOTE]
> Při kopírování prostředků nebo objektů prostředků z jednoho souboru. RC do jiného může vizuál C++ změnit hodnotu symbolu převedeného prostředku nebo název symbolu a hodnotu, aby nedocházelo ke konfliktům s názvy symbolů nebo hodnotami v existujícím souboru.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>
