---
title: 'Symboly: Identifikátory prostředků | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.identifiers
dev_langs:
- C++
helpviewer_keywords:
- symbols, resource identifiers
- symbols, creating
- resource symbols
- symbols, editing
- resource editors, resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d1914f13a74a9af33fc2008f759062ea22c20c5b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604335"
---
# <a name="symbols-resource-identifiers"></a>Symboly: identifikátory prostředků

Symbol je identifikátor prostředku (ID), který se skládá ze dvou částí: textový řetězec (název symbolu) mapovat na celočíselnou hodnotu (hodnoty symbolů). Příklad:

```
IDC_EDITNAME = 5100
```

Názvy symbolů se často označují jako identifikátory.

Symboly zadejte popisný způsob, jak odkazující na prostředky a objekty uživatelského rozhraní, ve zdrojovém kódu a při práci s nimi v editory prostředků. Můžete zobrazit a pracovat s symboly pomocí jednoho vhodným místem [symboly prostředků – dialogové okno](../windows/viewing-resource-symbols.md).

Když vytvoříte nový prostředek nebo prostředek objektu [editory prostředků](../windows/resource-editors.md) zadejte výchozí název prostředku, například `IDC_RADIO1`a přiřadit hodnotu. Definice name plus hodnota je uložena v souboru Resource.h.

> [!NOTE]
> Při do jiné kopírování prostředků nebo objektů prostředků z jednoho souboru .rc, Visual C++ může změnit přenesené prostředek hodnota symbolu, nebo názvu symbolu a hodnotu, aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty v existující soubor.

S růstem vaší aplikace v velikost i sofistikovanější postupy zločinců se počet zdrojů a symbolů. Sledování velký počet symbolů, které jsou rozmístěny v několika souborů. může být obtížné. [Symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md) zjednodušuje správu symbol tím, že nabízí centrální nástroj, pomocí kterého můžete:

- [Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)

- [Vytváření nových symbolů](../windows/creating-new-symbols.md)

- [Změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md)

- [Odstranění nepřiřazených symbolů](../windows/deleting-unassigned-symbols.md)

- [Otevření editoru prostředků pro daný Symbol](../windows/opening-the-resource-editor-for-a-given-symbol.md)

- [Změna symbolu nebo názvu symbolu (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Změna číselné hodnoty symbolu](../windows/changing-a-symbol-s-numeric-value.md)

- [Změna názvů hlavičkových souborů symbolu](../windows/changing-the-names-of-symbol-header-files.md)

- [Zahrnout sdílených (jen pro čtení) nebo vypočtených symbolů](../windows/including-shared-read-only-or-calculated-symbols.md)

- [Zobrazit ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Vyhledávání symbolů v prostředcích](../windows/how-to-search-for-symbols-in-resources.md)  
[Editory prostředků](../windows/resource-editors.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)