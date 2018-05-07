---
title: Podpora průvodce pro jiné jazyky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.EastAsianLanguages
dev_langs:
- C++
helpviewer_keywords:
- wizards [C++], language support
- language support for MFC projects
- projects [C++], language support
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75aafd7177c3799c17b75419fd5ab9f54af91d35
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wizard-support-for-other-languages"></a>Podpora průvodce pro ostatní jazyky
Při instalaci sady Visual Studio, instalační program aplikace zjistí národní prostředí uvedené ve vašem systému a nainstaluje odpovídající jazyk šablony nebo šablony pro toto národní prostředí. Například pro prostředí západní Evropy, instalační program nainstaluje angličtina, francouzština, italština, španělština a němčina. Tyto jazyky se zobrazí v **jazyk prostředku** seznam na [typ aplikace](../mfc/reference/application-type-mfc-application-wizard.md) stránky Průvodce aplikací MFC.  
  
## <a name="language-templates"></a>Šablony v jazyce  
 Ne všechny šablony jsou nainstalováni na všech systémech, protože šablony jsou založené na kódování ANSI, a ne všechny prostředky lze upravovat na všech systémech. Ve výchozím nastavení, například nelze upravit japonské prostředky ve francouzštině systému.  
  
 Pokud používáte systém Windows 2000 nebo novější a chcete vytvořit aplikaci MFC v jiném jazyce, pak musíte zkopírovat adresáři šablony pro příslušný jazyk z média instalační program sady Visual Studio (Disk 1) do systému.  
  
> [!NOTE]
>  Chcete-li upravit vytvořený projekt, musíte nastavit národní prostředí systému na příslušné národní prostředí pro vybraný jazyk.  
  
 Šablony jsou že každé přiřadit do složky v adresáři \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\, jak je uvedeno v následující tabulce. Pro přístup k šabloně požadovaný jazyk, zkopírujte příslušné složky do adresáře \mfcappwiz\templates\ ve vašem počítači. Jakmile jste zkopírovali složku, objeví se jazyk v **jazyk prostředku** seznam na **typ aplikace** stránky Průvodce aplikací MFC.  
  
### <a name="language-templates-provided-in-visual-studio-net"></a>Šablony v jazyce zadaný v sadě Visual Studio .NET  
  
|Jazyk|Šablony|  
|--------------|--------------|  
|Čínština (tradiční)|1028|  
|Čínština (zjednodušená)|2052|  
|Angličtina|1033|  
|Francouzština|1036|  
|Němčina|1031|  
|Italština|1040|  
|Japonština|1041|  
|Korejština|1042|  
|Španělština|3082|  
  
## <a name="format-of-visual-c-wizard-generated-files"></a>Formát souborů Visual C++ generovaných průvodcem  
 Průvodci Visual C++ vygeneruje projekty v kódu Unicode, když nainstalovaný jazyk verze sady Visual Studio neodpovídá národního prostředí. Například když japonské verze sady Visual Studio je nainstalován na počítači, který má místní nastavení nastavena na jakémkoli jiném jazyce než japonštině, pak Visual C++ generovat projekty tvořené soubory Unicode. To je běžné v počítačích s Windows více jazykové (sady MUI Multilingual) sady.  
  
 Toto chování se liší od systémů, takže národního prostředí je stejný jako jazyková verze sady Visual Studio. V takovém případě projektu soubory budou vytvořeny v ANSI v systému znaková stránka.  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Vytváření a správa projektů Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)