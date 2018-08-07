---
title: Otevření prostředku pro binární úpravy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 428c62db8f1444f497d6fede7affea34560b4b0e
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605952"
---
# <a name="opening-a-resource-for-binary-editing"></a>Otevření prostředku pro binární úpravy
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Chcete-li otevřít prostředek klasické pracovní plochy Windows pro binární úpravy  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), vyberte soubor konkrétní prostředek, který chcete upravit.  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Klikněte pravým tlačítkem na zdroj a klikněte na tlačítko **Open binární Data** z místní nabídky.  
  
    > [!NOTE]
    >  Pokud používáte [zobrazení prostředků](../windows/resource-view-window.md) okno otevřít prostředek ve formátu, že Visual Studio nedokáže rozpoznat (například RCDATA nebo vlastní prostředek), prostředek se automaticky otevře v binárním editoru.  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>Otevřete spravovaný prostředek pro binární úpravy  
  
1.  V **Průzkumníka řešení**, vyberte soubor konkrétní prostředek, který chcete upravit.  
  
2.  Klikněte pravým tlačítkem na prostředek a zvolte **otevřít v** z místní nabídky.  
  
3.  V **otevřít v** dialogového okna zvolte **binární Editor**.  
  
    > [!NOTE]
    >  Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.  
  
    > [!NOTE]
    >  Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).   
  
 ![Binární Editor](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
Binární Data pro dialogové okno se zobrazí v binárním editoru  
  
 Jenom konkrétní hodnoty ASCII jsou reprezentovány v binárním editoru (0x20 prostřednictvím 0x7E). Rozšířené znaky zobrazují jako tečky v části hodnotu ASCII binární editor (pravý panel). "Tisknutelné" znaky jsou hodnoty ASCII 32 prostřednictvím 126.  
  
> [!NOTE]
>  Pokud chcete použít binární editor prostředku už upravována v jiném okně editoru, nejprve zavřete ostatní okna editoru.  
  
## <a name="requirements"></a>Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Binární editor](binary-editor.md)