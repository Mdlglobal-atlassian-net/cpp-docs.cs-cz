---
title: Vytvoření nového tlačítka panelu nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar
dev_langs:
- C++
helpviewer_keywords:
- Toolbar editor, creating buttons
- toolbar buttons (in Toolbar editor), button image
- toolbar buttons (in Toolbar editor), creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 737c517a2c92d07a6d5110b0bcc08f0d9a290f5e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603169"
---
# <a name="creating-a-new-toolbar-button"></a>Vytvoření nového tlačítka panelu nástrojů

### <a name="to-create-a-new-toolbar-button"></a>K vytvoření nového tlačítka panelu nástrojů

1. V [zobrazení prostředků](../windows/resource-view-window.md) rozbalte složku prostředků (například Project1.rc).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. Rozbalte **nástrojů** a pak zvolte položku panelu nástrojů pro úpravy.

3. Přiřaďte ID prázdné tlačítko na pravém konci panelu nástrojů. Můžete tak učinit pomocí úpravy **ID** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete například poskytnout stejný Identifikátor jako možnost nabídky tlačítka panelu nástrojů. V takovém případě použijte pole rozevíracího seznamu vyberte **ID** položky nabídky.

   -nebo-

   Vyberte tlačítko prázdné na pravém konci panelu nástrojů (v **panel nástrojů zobrazení** podokno) a začněte kreslení. Je přiřazen výchozí Identifikátor příkazu tlačítka (ID_BUTTON\<n >).

Můžete také zkopírovat a vložit obrázek do nového tlačítka panelu nástrojů.

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Chcete-li přidat bitovou kopii na panelu nástrojů jako tlačítko

1. V [zobrazení prostředků](../windows/resource-view-window.md), otevřete poklepáním panelu nástrojů.

2. Dále otevřete image, kterou chcete přidat na panel nástrojů.

   > [!NOTE]
   > Pokud obrázek otevřít v sadě Visual Studio, se otevře v **Image** editoru. Image můžete otevřít také v jiných aplikacích grafiky.

3. Z **upravit** nabídce zvolte **kopírování**.

4. Přepnout na panelu nástrojů kliknutím na jeho karty v horní části okna zdroje.

5. Z **upravit** nabídce zvolte **vložit**.

   Obrázek se zobrazí na panelu nástrojů jako nového tlačítka.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Knihovny MFC nebo ATL

## <a name="see-also"></a>Viz také

[Vlastnosti tlačítka panelu nástrojů](../windows/toolbar-button-properties.md)  
[Vytváření, přesunutí a úprava tlačítek panelu nástrojů](../windows/creating-moving-and-editing-toolbar-buttons.md)  
[Editor panelu nástrojů](../windows/toolbar-editor.md)