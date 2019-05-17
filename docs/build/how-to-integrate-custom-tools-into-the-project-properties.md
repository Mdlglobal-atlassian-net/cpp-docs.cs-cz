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

Můžete přidat vlastní nástroj možnosti sady Visual Studio **stránky vlastností** okna tak, že vytvoříte základního souboru schématu XML.

**Vlastnosti konfigurace** část **stránky vlastností** v okně se zobrazí skupiny nastavení, které jsou označovány jako *pravidla*. Každé pravidlo obsahuje nastavení pro nástroj nebo skupinu funkcí. Například **Linkeru** pravidlo obsahuje nastavení pro nástroj linker. Nastavení v pravidle dají rozdělit na *kategorie*.

Tento dokument vysvětluje, jak vytvořit soubor v adresáři sady, který obsahuje vlastnosti pro vlastní nástroj tak, aby vlastnosti jsou načteny při spuštění sady Visual Studio. Informace o tom, jak upravit soubor najdete v tématu [platformy Extensibilty část 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) na blogu týmu projektu Visual Studio.

### <a name="to-add-or-change-project-properties"></a>Přidání nebo změna vlastností projektu

1. V editoru XML vytvořte soubor XML.

1. Uložte soubor v sadě Visual Studio `VCTargets\1033` složky. Budete mít jinou cestu pro jednotlivé edice aplikace Visual Studio, který je nainstalován a jednotlivé jazyky. Například výchozí cesta ke složce pro edice Visual Studio Community. 2019 v angličtině je `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets`. Upravte cestu pro váš jazyk a edice sady Visual Studio. Každé pravidlo v **stránky vlastností** okna je reprezentována soubor XML v této složce. Ujistěte se, že soubor je jedinečně pojmenovaná ve složce.

1. Zkopírujte obsah `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` (nebo cokoli, co je vaše cesta) zavřete bez uložení změn a vložte obsah v novém souboru XML. Můžete použít libovolný soubor schématu XML – Toto je pouze jeden, který je možné, začněte šablonou.

1. V novém souboru XML upravte obsah podle vašich požadavků. Ujistěte se, že chcete-li změnit **název pravidla** a **Rule.DisplayName** v horní části souboru.

1. Uložte změny a zavřete soubor.

1. Soubory XML `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (nebo všude, kde jste uložili) jsou načteny při spuštění sady Visual Studio. Proto se nový soubor testu, restartujte aplikaci Visual Studio.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **vlastnosti**. V **stránky vlastností** okno, v levém podokně, ověřte, zda je nový uzel s názvem pravidla.

## <a name="see-also"></a>Viz také:

[MSBuild na příkazovém řádku - C++](msbuild-visual-cpp.md)
