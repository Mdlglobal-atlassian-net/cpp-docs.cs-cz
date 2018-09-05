---
title: 'Postupy: integrace vlastních nástrojů do vlastností projektu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 04/27/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.howto.integratecustomtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 047427c344e8768fafa984ac72984c968d60238f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693838"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Postupy: Integrace vlastních nástrojů do vlastností projektu
Můžete přidat vlastní nástroj možnosti sady Visual Studio **stránky vlastností** okna tak, že vytvoříte základního souboru schématu XML.  
  
 **Vlastnosti konfigurace** část **stránky vlastností** v okně se zobrazí skupiny nastavení, které jsou označovány jako *pravidla*. Každé pravidlo obsahuje nastavení pro nástroj nebo skupinu funkcí. Například **Linkeru** pravidlo obsahuje nastavení pro nástroj linker. Nastavení v pravidle dají rozdělit na *kategorie*.  
  
 Tento dokument vysvětluje, jak vytvořit soubor v adresáři sady, který obsahuje vlastnosti pro vlastní nástroj tak, aby vlastnosti jsou načteny při spuštění sady Visual Studio. Informace o tom, jak upravit soubor najdete v tématu [platformy Extensibilty část 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) na blogu týmu projektu Visual Studio.  
  
### <a name="to-add-or-change-project-properties"></a>Přidání nebo změna vlastností projektu  
  
1.  V editoru XML vytvořte soubor XML.  
  
2.  Uložte soubor do sady Visual Studio 2017 `VCTargets\1033` složky. Budete mít jinou cestu pro jednotlivé edice aplikace Visual Studio 2017, který je nainstalován a jednotlivé jazyky. Je třeba cesta ke složce pro Visual Studio Enterprise edition v angličtině `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Upravte cestu pro váš jazyk a edice sady Visual Studio. Každé pravidlo v **stránky vlastností** okna je reprezentována soubor XML v této složce. Ujistěte se, že soubor je jedinečně pojmenovaná ve složce.  
  
3.  Zkopírujte obsah `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`, zavřete bez uložení změn a vložte obsah v novém souboru XML. Můžete použít libovolný soubor schématu XML – Toto je pouze jeden, který je možné, začněte šablonou.  
  
4.  V novém souboru XML upravte obsah podle vašich požadavků. Ujistěte se, že chcete-li změnit **název pravidla** a **Rule.DisplayName** v horní části souboru.  
  
5.  Uložte změny a zavřete soubor.  
  
6.  Soubory XML `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` jsou načteny při spuštění sady Visual Studio. Proto se nový soubor testu, restartujte aplikaci Visual Studio.  
  
7.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **vlastnosti**. V **stránky vlastností** okno, v levém podokně, ověřte, zda je nový uzel s názvem pravidla.  
  
## <a name="see-also"></a>Viz také  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
