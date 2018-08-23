---
title: Změna vlastností vícenásobných kláves akcelerátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0b24d69a080e9022f7682ba89b6cdf7cb99ce5ca
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592148"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys"></a>Změna vlastností vícenásobných kláves akcelerátoru

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Změna vlastností vícenásobných kláves akcelerátoru

1. Otevřete poklepáním na ikonu v tabulce akcelerátorů [zobrazení prostředků](../windows/resource-view-window.md).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Vyberte klávesy akcelerátoru chcete změnit tím, že se **Ctrl** klíče při klepnutí na každé z nich.

3. Přejděte [okno vlastností](/visualstudio/ide/reference/properties-window) a zadejte hodnoty, které chcete všechny vybrané akcelerátorů sdílet.

   > [!NOTE]
   > Každá hodnota modifikátor se zobrazí jako vlastnost typu Boolean v **vlastnosti** okna. Pokud změníte [modifikátor](../windows/accelerator-modifier-property.md) hodnotu **vlastnosti** okně tabulky akcelerátorů považuje za new – modifikátor doplněk žádné modifikátory, které byly dříve. Proto pokud nastavíte všechny hodnoty modifikátor budete muset nastavit všechny z nich zajistit, že každý akcelerátor sdílí stejný **modifikátor** nastavení.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Úprava tabulek akcelerátorů](../windows/editing-accelerator-tables.md)  
[Editor akcelerátorů](../windows/accelerator-editor.md)