---
title: Zobrazení a úprava prostředků v editoru prostředků (C++)
ms.date: 11/04/2016
f1_keywords:
- vs.resourceview
helpviewer_keywords:
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
ms.openlocfilehash: b33b7b52f494971451298e0827327cc86e60e7f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582622"
---
# <a name="viewing-and-editing-resources-in-a-resource-editor-c"></a>Zobrazení a úprava prostředků v editoru prostředků (C++)

Každý typ prostředku má **prostředků** editor specifické pro příslušný typ prostředku. Můžete změnit uspořádání, změňte velikost, přidat ovládací prvky a funkce nebo jinak upravit aspektů prostředku pomocí editoru přidružené. Můžete také upravit prostředek v [textový formát](../windows/how-to-open-a-resource-script-file-in-text-format.md) a [binární formát](../windows/opening-a-resource-for-binary-editing.md).

Některé typy prostředků jsou jednotlivé soubory, které můžete importovat a používat různými způsoby; patří mezi ně rastrové obrázky, ikony, kurzory, panely nástrojů a soubory html. Tyto zdroje mají názvy souborů a jednak [identifikátory prostředků](../windows/symbols-resource-identifiers.md). Jiné, jako je například dialogová okna, nabídek a tabulky řetězců v projekty Win32, existují pouze v rámci prostředku skriptů (.rc) souboru nebo souboru prostředků (.rct) šablony.

> [!NOTE]
> Vlastnosti prostředku [lze upravit pomocí okna vlastnosti](../windows/changing-the-properties-of-a-resource.md).

## <a name="win32-resources"></a>Prostředky Win32

Budete mít přístup k prostředkům Win32 v [zobrazení prostředků](../windows/resource-view-window.md) podokně.

### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Chcete-li zobrazit prostředek systému Win32 v editoru prostředků

1. Vyberte **zobrazení prostředků** z **zobrazení** nabídky.

2. Pokud **zobrazení prostředků** není úplně nahoře okno, klikněte na tlačítko **zobrazení prostředků** kartu a přenést ho do horní části.

3. Z **zobrazení prostředků**, rozbalte složku pro projekt, který obsahuje prostředky, které chcete zobrazit. Například pokud chcete zobrazit prostředku dialogového okna, rozbalte **dialogové okno** složky.

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

4. Dvakrát klikněte na prostředek, třeba **IDD_ABOUTBOX**.

   Prostředek se otevře ve vhodném editoru. Například pro prostředky dialogového okna, prostředek se otevře uvnitř **dialogové okno** editoru.

   Můžete také [zobrazit prostředky v souboru .rc (skript prostředků) bez nutnosti otevřít projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-delete-an-existing-win-32-resource"></a>Chcete-li odstranit existující prostředek Win 32

1. V **zobrazení prostředků**, rozbalte uzel pro typ prostředku.

2. Klikněte pravým tlačítkem na požadovaný prostředek odstranit a zvolit **odstranit** z místní nabídky.

   > [!NOTE]
   > Můžete odstranit prostředků pomocí příkazu stejné místní nabídky v případě, že máte soubor .rc otevřený v okna dokumentu mimo projekt.

## <a name="resources-in-managed-projects"></a>Prostředky ve spravovaných projektech

Protože spravované projekty nepoužívají soubory skriptu prostředků, je nutné otevřít prostředky z **Průzkumníka řešení**. Můžete použít [editor obrázků](../windows/image-editor-for-icons.md) a [binární editor](binary-editor.md) pro práci se soubory prostředků ve spravovaných projektech. Všechny spravované prostředky, které chcete upravit, musí být propojené prostředky. Editory prostředků Visual Studio nepodporují úpravy vložených prostředků.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>Chcete-li zobrazit spravovaných prostředků v editoru prostředků

1. V **Průzkumníka řešení**, dvakrát klikněte na prostředek, třeba **Bitmap1.bmp**.

   Prostředek se otevře ve vhodném editoru.

### <a name="to-delete-an-existing-managed-resource"></a>Chcete-li odstranit existující spravovaný prostředek

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na požadovaný prostředek odstranit a zvolit **odstranit** z místní nabídky.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Editory prostředků](../windows/resource-editors.md)