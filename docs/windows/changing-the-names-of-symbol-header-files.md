---
title: Změna názvů hlavičkových souborů symbolu
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing.header
helpviewer_keywords:
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
ms.openlocfilehash: 4d9aa350d0f680e975c68bf46ac066072df044cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432331"
---
# <a name="changing-the-names-of-symbol-header-files"></a>Změna názvů hlavičkových souborů symbolu

Obvykle všechny symbol definice jsou uložené v `Resource.h`. Však může být nutné změnit to zahrnovat název souboru, což umožní, například pracovat s více než jeden soubor prostředků ve stejném adresáři.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Chcete-li změnit název hlavičkový soubor symbolů prostředků

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a zvolte [prostředek zahrnuje](../windows/resource-includes-dialog-box.md) z místní nabídky.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V **hlavičkový soubor symbolů** zadejte nový název pro tento soubor.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)<br/>
[ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)