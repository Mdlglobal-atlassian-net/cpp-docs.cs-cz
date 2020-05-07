---
title: 'Postupy: Integrace vlastních nástrojů do vlastností projektu'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 0c0233ad6715a3adb7d47f021a87207f288d5139
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837032"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Postupy: Integrace vlastních nástrojů do vlastností projektu

Můžete přidat vlastní možnosti nástrojů do okna **stránky vlastností** aplikace Visual Studio vytvořením základního souboru schématu XML.

V části **Vlastnosti konfigurace** v okně **stránky vlastností** se zobrazují skupiny nastavení, které se nazývají *pravidla*. Každé pravidlo obsahuje nastavení pro nástroj nebo skupinu funkcí. Například pravidlo **linkeru** obsahuje nastavení pro nástroj linkeru. Nastavení v pravidle lze rozdělit do *kategorií*.

Tento dokument vysvětluje, jak vytvořit soubor v adresáři množiny, který obsahuje vlastnosti vlastního nástroje, aby byly vlastnosti načteny při spuštění sady Visual Studio. Informace o tom, jak upravit soubor, najdete v tématu [Extensibilty platformy část 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) na blogu týmu projektu sady Visual Studio.

### <a name="to-add-or-change-project-properties"></a>Chcete-li přidat nebo změnit vlastnosti projektu

1. V editoru XML vytvořte soubor XML.

1. Uložte soubor ve složce sady Visual Studio `VCTargets\1033` . Budete mít jinou cestu pro každou edici sady Visual Studio, která je nainstalována a každý jazyk. Například výchozí cesta ke složce pro Visual Studio 2019 Community Edition v angličtině je `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets`. Upravte cestu pro jazyk a edici sady Visual Studio. Každé pravidlo v okně **stránky vlastností** je reprezentováno souborem XML v této složce. Přesvědčte se, zda je soubor jednoznačně pojmenován ve složce.

1. Zkopírujte obsah `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` (nebo libovolnou cestu), zavřete jej bez uložení změn a pak vložte obsah do nového souboru XML. Můžete použít libovolný soubor schématu XML – to je jenom ten, který se dá použít, abyste mohli začít s šablonou.

1. V novém souboru XML upravte obsah podle vašich požadavků. Ujistěte se, že jste změnili **název pravidla** a **pravidlo. DisplayName** v horní části souboru.

1. Uložte změny a zavřete soubor.

1. Soubory XML v `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (nebo kdekoli, kde jste je uložili) jsou načteny při spuštění sady Visual Studio. Proto pro otestování nového souboru restartujte aplikaci Visual Studio.

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a pak klikněte na **vlastnosti**. V okně **stránky vlastností** v levém podokně ověřte, zda je k dispozici nový uzel s názvem vašeho pravidla.

## <a name="see-also"></a>Viz také

[MSBuild na příkazovém řádku – C++](msbuild-visual-cpp.md)
