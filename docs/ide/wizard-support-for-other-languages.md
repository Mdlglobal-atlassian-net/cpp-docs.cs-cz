---
title: Podpora průvodce pro ostatní jazyky | Dokumentace Microsoftu
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
ms.openlocfilehash: c33858e02fd8bad03e03a963e940f215d528157d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395128"
---
# <a name="wizard-support-for-other-languages"></a>Podpora průvodce pro ostatní jazyky

Při instalaci sady Visual Studio, instalační program aplikace zjistí národního prostředí uvedený ve vašem systému a nainstaluje se příslušný jazyk šablony nebo šablony pro toto národní prostředí. Například pro prostředí západní Evropy, instalační program nainstaluje angličtina, francouzština, italština, španělština a němčina. Tyto jazyky se zobrazí v **jazyk prostředku** seznamu [typ aplikace](../mfc/reference/application-type-mfc-application-wizard.md) stránky Průvodce aplikací knihovny MFC.

## <a name="language-templates"></a>Šablony jazyka

Na všech systémech, nejsou nainstalovány všechny šablony, protože šablony jsou založené na kódování ANSI, a ne všechny prostředky lze upravovat ve všech systémech. Ve výchozím nastavení, například nelze upravovat japonské prostředky ve francouzské systému.

Pokud používáte Windows 2000 nebo novější a chcete vytvořit aplikaci knihovny MFC v jiném jazyce, pak musíte zkopírovat adresář šablon pro příslušný jazyk z médií instalačního programu sady Visual Studio (Disk 1) do vašeho systému.

> [!NOTE]
>  Chcete-li upravit vytvořený projekt, musíte nastavit národní prostředí systému odpovídající národní prostředí pro vybraný jazyk.

Šablony jsou, že každý přiřazenou složku v adresáři \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\, jak je uvedeno v následující tabulce. Pro přístup k šabloně požadovaný jazyk, zkopírujte do adresáře \mfcappwiz\templates\ ve vašem počítači do příslušné složky. Po zkopírování složce jazyk se zobrazí v **jazyk prostředku** seznamu **typ aplikace** stránky Průvodce aplikací knihovny MFC.

### <a name="language-templates-provided-in-visual-studio-net"></a>Šablony jazyka, které jsou k dispozici v sadě Visual Studio .NET

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

Průvodce Visual C++ vygeneruje projekty v kódování Unicode, když nainstalované jazykové verzi sady Visual Studio se neshoduje s národního prostředí. Například při instalaci japonské verze sady Visual Studio na počítači, který má místní nastavení nastavena na jiném jazyku, než japonština, pak průvodce Visual C++ vygeneruje projekty sestává z soubory Unicode. To je běžné v počítačích s Windows, více jazykových sad (sady MUI).

Toto chování se liší od systémů, které se národního prostředí je stejná jako verze jazyka sady Visual Studio. V takovém případě se soubory projektu vytvoří v ANSI v znaková stránka systému.

## <a name="see-also"></a>Viz také

[Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)<br>
[Vytváření a spravování projektů Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)