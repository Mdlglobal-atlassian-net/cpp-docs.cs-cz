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
ms.openlocfilehash: c76b870ad1fdfeda7370af03c6396bedba9530ab
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954858"
---
# <a name="resource-identifiers-symbols-c"></a>Identifikátory prostředků (symbolů) (C++)

Symbol je identifikátor prostředku (ID), který se skládá ze dvou částí: textový řetězec (název symbolu) mapovat na celočíselnou hodnotu (hodnoty symbolů). Příklad:

```
IDC_EDITNAME = 5100
```

Názvy symbolů se často označují jako identifikátory.

Symboly zadejte popisný způsob, jak odkazující na prostředky a objekty uživatelského rozhraní, ve zdrojovém kódu a při práci s nimi v editory prostředků. Můžete zobrazit a pracovat s symboly pomocí jednoho vhodným místem [symboly prostředků – dialogové okno](../windows/viewing-resource-symbols.md).

Když vytvoříte nový prostředek nebo prostředek objektu [editory prostředků](../windows/resource-editors.md) zadejte výchozí název prostředku, například `IDC_RADIO1`a přiřadit hodnotu. Definice name plus hodnota je uložena v `Resource.h` souboru.

> [!NOTE]
> Při do jiné kopírování prostředků nebo objektů prostředků z jednoho souboru .rc, Visual C++ může změnit přenesené prostředek hodnota symbolu, nebo názvu symbolu a hodnotu, aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty v existující soubor.

S růstem vaší aplikace v velikost i sofistikovanější postupy zločinců se počet zdrojů a symbolů. Sledování velký počet symbolů, které jsou rozmístěny v několika souborů. může být obtížné. **Symbolů prostředků** dialogové okno zjednodušuje správu symbol tím, že nabízí centrální nástroj, pomocí kterého můžete:

- [Vytváření symbolů](../windows/creating-new-symbols.md)

- [Správa symbolů](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Zobrazit ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>