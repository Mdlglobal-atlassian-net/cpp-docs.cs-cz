---
title: Identifikátory prostředků (symbolů) (C++)
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
ms.openlocfilehash: 0b19ff0d1c709616868d47c172ff4cf8c6931b82
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036046"
---
# <a name="resource-identifiers-symbols-c"></a>Identifikátory prostředků (symbolů) (C++)

Symbol je identifikátor prostředku (ID), který se skládá ze dvou částí namapována na hodnotu symbol (celé číslo), třeba názvu symbolu (řetězec):

```
IDC_EDITNAME = 5100
```

Názvy symbolů se často označují jako identifikátory.

Symboly zadejte popisný způsob, jak odkazující na prostředky a objekty uživatelského rozhraní, ve zdrojovém kódu a při práci s nimi v editory prostředků. Můžete zobrazit a pracovat s symboly pomocí jednoho vhodným místem [symboly prostředků – dialogové okno](../windows/viewing-resource-symbols.md).

S růstem vaší aplikace v velikost i sofistikovanější postupy zločinců se počet zdrojů a symbolů. Sledování velký počet symbolů, které jsou rozmístěny v několika souborů. může být obtížné. **Symbolů prostředků** dialogové okno zjednodušuje správu symbol tím, že nabízí centrální nástroj, pomocí kterého můžete:

- [Vytváření symbolů](../windows/creating-new-symbols.md)

- [Správa symbolů](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Zobrazit ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)

Když vytvoříte nový prostředek nebo prostředek objektu [editory prostředků](../windows/resource-editors.md) zadejte výchozí název prostředku, například `IDC_RADIO1`a přiřadit hodnotu. Definice name plus hodnota je uložena v `Resource.h` souboru.

> [!NOTE]
> Při do jiné kopírování prostředků nebo objektů prostředků z jednoho souboru .rc, Visual C++ může změnit přenesené prostředek hodnota symbolu, nebo názvu symbolu a hodnotu, aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty v existující soubor.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Zdrojové soubory](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>