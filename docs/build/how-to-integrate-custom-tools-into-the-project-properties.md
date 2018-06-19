---
title: 'Postupy: integrace vlastních nástrojů do vlastností projektu | Microsoft Docs'
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
ms.openlocfilehash: 00482aa2b4b700d15e46d0741e76dd17afc28419
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368899"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Postupy: Integrace vlastních nástrojů do vlastností projektu
Možnosti vlastního nástroje můžete přidat do sady Visual Studio **stránky vlastností** okna tak, že vytvoříte základní souboru schématu XML.  
  
 **Vlastnosti konfigurace** části **stránky vlastností** v okně se zobrazí skupiny nastavení, které jsou známé jako *pravidla*. Každé pravidlo obsahuje nastavení pro nástroj nebo skupiny funkcí. Například **Linkeru** pravidlo obsahuje nastavení pro nástroj linkeru. Nastavení v pravidle lze rozdělit na *kategorie*.  
  
 Tento dokument vysvětluje, jak vytvořit soubor v adresáři sady, který obsahuje vlastnosti pro svůj vlastní nástroj tak, aby vlastnosti jsou načteny při spuštění sady Visual Studio. Informace o tom, jak upravit soubor najdete v tématu [platformy Extensibilty část 2](http://go.microsoft.com/fwlink/p/?linkid=191489) na blogu týmu projekt Visual Studio.  
  
### <a name="to-add-or-change-project-properties"></a>Chcete-li přidat nebo změnit vlastnosti projektu  
  
1.  V editoru XML vytvořte soubor XML.  
  
2.  Uložte soubor v aplikaci Visual Studio 2017 `VCTargets\1033` složky. Budete mít jinou cestu pro každou verzi Visual Studio 2017, který je nainstalován a jednotlivé jazyky. Je třeba cesta ke složce pro Visual Studio Enterprise edition v angličtině `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Upravte cestu pro jazyk a edicí sady Visual Studio. Každé pravidlo v **stránky vlastností** okno je reprezentována soubor XML v této složce. Ujistěte se, že soubor je jednoznačně s názvem ve složce.  
  
3.  Zkopírujte obsah `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`, zavřete bez uložení změn a vložte obsah v novém souboru XML. Můžete použít libovolný soubor schématu XML - Toto je pouze jeden, který lze použít, takže spuštění pomocí šablony.  
  
4.  V nový soubor XML upravíte obsah podle svých požadavků. Ujistěte se, chcete-li změnit **název pravidla** a **Rule.DisplayName** v horní části souboru.  
  
5.  Uložte změny a zavřete soubor.  
  
6.  Soubory XML `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` se načtou při spuštění sady Visual Studio. Proto otestovat nový soubor, restartujte Visual Studio.  
  
7.  V **Průzkumníku řešení**klikněte pravým tlačítkem na projekt a pak klikněte na tlačítko **vlastnosti**. V **stránky vlastností** okno, v levém podokně, ověřte, zda je nový uzel s názvem pravidla.  
  
## <a name="see-also"></a>Viz také  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
