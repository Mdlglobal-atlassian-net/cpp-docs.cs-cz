---
title: 'Postupy: kopírování prostředků (C++) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc0fc8f3177baa01742df84c926a3c6421aa9a16
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314573"
---
# <a name="how-to-copy-resources-c"></a>Postupy: kopírování prostředků (C++)

Prostředky můžete zkopírovat z jednoho souboru do jiného beze změny nebo se dají [Změna jazyka nebo podmínky prostředku během kopírování jeho](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).

Prostředky můžete snadno zkopírovat z existující prostředek nebo spustitelného souboru k aktuálnímu souboru prostředků. K tomuto účelu můžete otevřete oba soubory, které obsahují prostředky ve stejnou dobu a přetáhněte položky z jednoho souboru nebo kopírování a vkládání mezi dva soubory. Tato metoda se dá použít pro soubory skriptů (.rc) prostředků a soubory prostředků šablon (.rct), jakož i spustitelné soubory (.exe).

> [!NOTE]
> Visual C++ obsahuje ukázkové soubory prostředků, které můžete použít ve své aplikaci. Další informace najdete v tématu [Klipart: běžným prostředkům](https://github.com/Microsoft/VCSamples).

Můžete použít metodu a přetažení mezi soubory .rc, které jsou otevřené [mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Kopírování prostředků mezi soubory pomocí přetahování myší – metoda

1. Otevřete oba samostatné soubory prostředků (Další informace najdete v tématu [zobrazení prostředků, ve který #zahrnuje konce souboru mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Například otevřete Source1.rc a Source2.rc.

2. V prvním .rc souboru klikněte na prostředek, který chcete kopírovat. Například v `Source1.rc`, klikněte na tlačítko **IDD_DIALOG1**.

3. Podržte stisknutou klávesu CTRL a přetáhněte prostředek do druhého souboru .rc. Například, přetáhněte **IDD_DIALOG1** z `Source1.rc` k `Source2.rc`.

   > [!NOTE]
   > Přetažení prostředku bez podržení **Ctrl** klíč přesunu prostředku místo jeho kopírování.

### <a name="to-copy-resources-using-copy-and-paste"></a>Kopírování prostředků pomocí kopírování a vložení

1. Otevřete oba samostatné soubory prostředků (Další informace najdete v tématu [zobrazení prostředků, ve který #zahrnuje konce souboru mimo projekt](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Například Source1.rc a Source2.rc.

2. Ve zdrojovém souboru, ze kterého chcete kopírovat prostředek (například `Source1.rc`), klikněte pravým tlačítkem na prostředek a zvolte **kopírování** z místní nabídky.

3. Klikněte pravým tlačítkem na soubor prostředků, do které chcete vložit prostředku (například `Source2.rc`). Zvolte **vložit** z místní nabídky.

   > [!NOTE]
   > Nelze přetáhnout a vyřadit, kopírování, vyjmutí nebo vložte mezi soubory prostředků v projektu (**zobrazení prostředků**) a samostatné .rc soubory (ty otevřít v systému windows dokumentu). Můžete to udělat v předchozích verzích produktu.

   > [!NOTE]
   > Aby nedocházelo ke konfliktům s názvy symbolů nebo hodnoty v existující soubor, Visual C++ změnit hodnotu symbolu přenesené prostředků nebo název symbolu a hodnota při kopírování do nového souboru.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Postupy: Otevření souboru skriptu prostředků mimo projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
[Soubory prostředků](../windows/resource-files-visual-studio.md)  
[Editory prostředků](../windows/resource-editors.md)