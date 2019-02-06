---
title: 'Postupy: Vytvořit prostředek (C++)'
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- resources [C++], viewing
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
ms.assetid: aad44914-9145-45a3-a7d8-9de89b366716
ms.openlocfilehash: fdf158bab7894497dbcfb147eb2c6e061879be75
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55764048"
---
# <a name="how-to-create-a-resource-c"></a>Postupy: Vytvořit prostředek (C++)

**Zobrazení prostředků** okno zobrazuje soubory prostředků zahrnuté v projektech. Typy prostředků pro daný soubor .rc lze zobrazit rozbalením složky nejvyšší úrovně (například Project1.rc). Rozbalením libovolného typu prostředku lze zobrazit jednotlivé prostředky daného typu.

> [!NOTE]
> Tyto informace se nevztahují na prostředky v aplikacích pro univerzální platformu Windows. Další informace o tom najdete v tématu [prostředků aplikace a systém správy zdrojů](/windows/uwp/app-resources/).

> [!NOTE]
> **Zobrazení prostředků** není podporováno ve verzích Express.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

**Zobrazení prostředků** okno používá **přidat prostředek** dialogové okno Přidat prostředky do projektu aplikace klasické pracovní plochy Windows C++. Dialogové okno obsahuje následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Typ prostředku**|Určuje typ prostředku, který chcete vytvořit.<br/><br/>Lze rozbalit kategorie prostředků kurzoru a dialogového okna, čímž odhalíte další prostředky. Tyto prostředky jsou umístěny v ...\Microsoft Visual Studio `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Pokud přidáte soubory .rct, je nutné umístit do tohoto adresáře nebo je nutné zadat [zahrnout cestu](../windows/how-to-specify-include-directories-for-resources.md) pro ně. Prostředky v těchto souborech se potom objeví na druhé úrovni pod příslušnou kategorií. Není nijak omezený počet souborů .rct, můžete přidat.<br/><br/>Prostředky zobrazené na nejvyšší úrovni stromové struktury jsou výchozí prostředky, které jsou k dispozici v systému Visual Studio.|
|**Nové**|Vytvoří prostředek v závislosti na typu vámi zvolená v **typ prostředku** pole. Prostředek se otevře ve vhodném editoru. Například pokud vytvoříte prostředek dialogového okna, otevře se v [editoru dialogového okna](../windows/dialog-editor.md).|
|**Import**|Otevře **importovat** dialogovému oknu, ve kterém můžete přejít k prostředku můžete chtít importovat do aktuálního projektu. Lze importovat bitmapy, ikony, kurzory, soubory prostředků v jazyce HTML, soubory zvukových prostředků (.WAV) nebo soubory vlastních prostředků.|
|**Vlastní**|Otevře **nový vlastní prostředek** dialogovému oknu, ve kterém můžete vytvořit vlastní prostředek. Vlastní prostředky lze upravovat pouze v binárním editoru.|

**Nový vlastní prostředek** dialogové okno umožňuje vytvořit nový vlastní prostředek v projektu jazyka C++. Toto dialogové okno má následující vlastnost:

|Vlastnost|Popis|
|---|---|
|**Typ prostředku**|Obsahuje textové pole pro zadání názvu vlastní typ prostředku. Visual C++ automaticky změní na velké název při ukončení **nový vlastní prostředek** dialogové okno.|

Při vytváření nového prostředku jazyka Visual C++ přiřadí jedinečný název, například `IDD_Dialog1`. Toto ID prostředku lze přizpůsobit úpravou vlastností pro prostředek v editoru přidružený prostředek nebo v [okno vlastností](/visualstudio/ide/reference/properties-window).

Prostředek můžete vytvořit jako nové výchozí prostředek (prostředek, který není založen na šabloně) nebo jako prostředek vzorované po [šablony](../windows/how-to-use-resource-templates.md).

> [!NOTE]
> Nezadávejte název prostředku nebo ID, který je vyhrazený pro Visual Studio. Vyhrazené názvy jsou DESIGNINFO, HWB a TEXTINCLUDE a vyhrazené ID je 255.

## <a name="to-open-the-resource-view-window"></a>Otevření okna Zobrazení prostředků

Vyberte **zobrazení prostředků** na **zobrazení** nabídky.

   \- nebo –

Stisknutím klávesy **Ctrl** + **Shift** + **E**.

> [!TIP]
> Klepnutí pravým tlačítkem myši na **zobrazení prostředků** okno místní nabídku příkazů. Dvojitým kliknutím na záhlaví lze okno také ukotvit nebo uvolnit. Kliknutím na záhlaví pravým tlačítkem zobrazíte dodatečné příkazy, kterými lze ovládat chování okna. Další informace najdete v tématu [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

## <a name="to-create-a-new-resource-in-resource-view"></a>Chcete-li vytvořit nový prostředek v okně zobrazení prostředků

1. Se zaměřením na souboru .rc v **zobrazení prostředků**, vyberte **upravit** nabídku a zvolte **přidat prostředek** (nebo klikněte pravým tlačítkem na soubor .rc v **zobrazení prostředků** a zvolte **přidat prostředek** z místní nabídky).

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V **přidat prostředek** dialogové okno Vyberte typ prostředku, které chcete přidat do projektu.

## <a name="to-create-a-new-resource-in-solution-explorer"></a>Chcete-li vytvořit nový prostředek v Průzkumníku řešení

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na složku projektu a zvolte **přidat**, pak klikněte na tlačítko **přidat prostředek** v místní nabídce.

   Pokud ještě nemáte souboru .rc v projektu, tento krok ho vytvoří. Opakujte tento krok a přidejte konkrétní typy prostředků do nového souboru .rc.

2. V **přidat prostředek** dialogové okno Vyberte typ prostředku, které chcete přidat do projektu.

## <a name="to-create-a-new-resource-in-class-view"></a>Chcete-li vytvořit nový prostředek v zobrazení tříd

1. V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na vaší třídy a zvolte **přidat**a pak vyberte **přidat prostředek** z místní nabídky.

2. V **přidat prostředek** dialogové okno Vyberte typ prostředku, které chcete přidat do projektu.

## <a name="to-create-a-new-resource-from-the-project-menu"></a>Chcete-li vytvořit nový prostředek z nabídky Projekt

Z **projektu** nabídce zvolte **přidat prostředek**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také:

[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)<br/>
[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>
