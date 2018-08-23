---
title: / SOURCELINK (Sourcelink zahrnout soubor PDB) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /sourcelink
dev_langs:
- C++
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 876373b5646790f9f8de0042442b2ab56d9d2971
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "40242840"
---
# <a name="sourcelink-include-sourcelink-file-in-pdb"></a>/ SOURCELINK (Sourcelink zahrnout soubor PDB)

Určuje konfigurační soubor SourceLink zahrnout do souboru PDB vygenerován linkerem.

## <a name="syntax"></a>Syntaxe

> **/ SOURCELINK:**_název souboru_

## <a name="arguments"></a>Arguments

*Název souboru*  
Určuje konfiguraci ve formátu JSON soubor, který obsahuje jednoduché mapování místní cesty souborů na adresy URL ve kterém se dá načíst zdrojový soubor pro zobrazení ladicím programem. Další informace o formátu tohoto souboru najdete v tématu [schématu JSON odkaz zdroje](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Poznámky

SourceLink je nezávislá systém správy jazyka a zdroje pro poskytování ladění zdrojového kód pro binární soubory. SourceLink se podporuje pro nativní binární soubory C++ v sadě Visual Studio 2017 verze 15.8 spuštění. Přehled SourceLink, naleznete v tématu [odkazu na zdroj](https://github.com/dotnet/designs/blob/master/accepted/diagnostics/source-link.md). Informace o tom, jak používat SourceLink ve vašich projektech a jak vygenerovat soubor SourceLink jako součást vašeho projektu, naleznete v tématu [pomocí SourceLink](https://github.com/dotnet/sourcelink#using-sourcelink).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>Nastavení parametru linkeru/sourcelink v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. V **další možnosti** přidejte **/sourcelink:**_filename_ a klikněte na tlačítko **OK** nebo **použít**uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
- Tato možnost nemá programový ekvivalent.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)  
