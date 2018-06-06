---
title: / DEFAULTLIB (zadat výchozí knihovnu) | Microsoft Docs
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.DefaultLibraries
- /defaultlib
dev_langs:
- C++
helpviewer_keywords:
- -DEFAULTLIB linker option
- DEFAULTLIB linker option
- /DEFAULTLIB linker option
- libraries, adding to list of
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9afcaa0e229ec34ba91b4d60a7a4fa9acec2d7e3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569778"
---
# <a name="defaultlib-specify-default-library"></a>/DEFAULTLIB (Zadat výchozí knihovnu)

Zadejte výchozí knihovnu, kterou chcete hledat externí odkazy.

## <a name="syntax"></a>Syntaxe

> **/ DEFAULTLIB**:_knihovny_

### <a name="arguments"></a>Arguments

|Argument|Popis|
|-|-|
*Knihovna*|Název knihovnu, kterou chcete hledat při rozpoznávání externí odkazy.

## <a name="remarks"></a>Poznámky

**/DEFAULTLIB** možnost přidá jeden *knihovny* do seznamu knihovny, které odkaz vyhledá při rozpoznávání odkazy. Knihovnu zadaným **/DEFAULTLIB** prohledají se po explicitně zadat na příkazovém řádku a před výchozí knihovny s názvem v soubory .obj knihovny.

Při použití bez argumentů, [/NODEFAULTLIB (ignorovat všechny výchozí knihovny)](../../build/reference/nodefaultlib-ignore-libraries.md) možnost přepsání všechny **/DEFAULTLIB**:*knihovny* možnosti. **/NODEFAULTLIB**:*knihovny* možnost přepsání **/DEFAULTLIB**:*knihovny* při stejné *knihovny*název je zadán v obou.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. V **další možnosti**, zadejte **/DEFAULTLIB**:*knihovny* možnost pro každou knihovnu pro vyhledávání. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

- [Nastavení možností linkeru](../../build/reference/setting-linker-options.md)
- [Možnosti linkeru](../../build/reference/linker-options.md)
