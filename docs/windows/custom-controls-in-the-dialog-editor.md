---
title: Vlastní ovládací prvky v editoru dialogového okna | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- Custom Control
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], templates
- custom controls [Visual Studio], dialog boxes
- custom controls [Visual Studio]
- dialog box controls, custom (user) controls
- Dialog editor, custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7329873b8f56b44904c38161e737d99d29efa580
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592983"
---
# <a name="custom-controls-in-the-dialog-editor"></a>Vlastní ovládací prvky v editoru dialogových oken

Editor dialogového okna umožňuje použít existující "vlastní" nebo "user" ovládacích prvků v poli šablony dialogového okna.

> [!NOTE]
> Vlastní ovládací prvky v tomto smyslu jsou by se zaměňovat s ovládacími prvky ActiveX. Ovládací prvky ActiveX se někdy označuje jako vlastní ovládací prvky OLE. Nepleťte si také, tyto ovládací prvky s ovládacími prvky vykreslované uživatelem ve Windows.

Tato funkce je určená k vám umožňují používat ovládací prvky než ty, které poskytl Windows. V době běhu ovládací prvek přidružen třídy okna (není stejná jako třída C++). Častější způsob, jak dosáhnout jednoho cíle je nainstalovat libovolný ovládací prvek, jako je statický ovládací prvek, ve vašem dialogovém okně. Pak v době spuštění v [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) fungovat, odeberte ovládacího prvku a nahraďte ji pomocí vlastního ovládacího prvku.

Toto je starý postup. Dnes doporučujeme ve většině případů k zápisu ovládací prvek ActiveX nebo podtřídou běžný ovládací prvek Windows.

Pro tyto ovládací prvky jste omezeni na:

- V dialogovém okně Nastavení umístění.

- Zadáním titulek.

- Identifikace název třídy ovládacího prvku Windows (kód vaší aplikace musí zaregistrovat ovládací prvek s tímto názvem).

- Zadáním šestnáctkovou hodnotu 32-bit, který nastaví styl ovládacího prvku.

- Nastavení rozšířené stylu.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)  
[Ovládací prvky](../mfc/controls-mfc.md)