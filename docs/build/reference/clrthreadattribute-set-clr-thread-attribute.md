---
title: -CLRTHREADATTRIBUTE (nastavení atributu vlákna modulu CLR) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.CLRThreadAttribute
dev_langs:
- C++
helpviewer_keywords:
- /CLRTHREADATTRIBUTE linker option
- -CLRTHREADATTRIBUTE linker option
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea5b75c9f0691ef74c35ed405d64fc3389c4fcd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705793"
---
# <a name="clrthreadattribute-set-clr-thread-attribute"></a>/CLRTHREADATTRIBUTE (Nastavit atribut vlákna modulu CLR)

Explicitně určete vláknový atribut pro vstupní bod programu CLR.

## <a name="syntax"></a>Syntaxe

```
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}
```

#### <a name="parameters"></a>Parametry

**MTA**<br/>
Aplikuje atribut MTAThreadAttribute na vstupní bod programu.

**NONE**<br/>
Stejné jako bez zadání /CLRTHREADATTRIBUTE.  Umožňuje CLR Common Language Runtime () nastavil výchozí vláknový atribut.

**STA**<br/>
Aplikuje atribut STAThreadAttribute na vstupní bod programu.

## <a name="remarks"></a>Poznámky

Nastavení atributu vlákna je platný pouze při vytváření .exe, jak to má vliv na vstupní bod z hlavního vlákna.

Pokud používáte výchozí vstupní bod (hlavní nebo wmain, například) určení modelu vláken s použitím /CLRTHREADATTRIBUTE nebo tak, že práce s vlákny atribut (atribut STAThreadAttribute nebo MTAThreadAttribute) na výchozí položku funkce.

Pokud používáte jiné než výchozí vstupní bod, určení modelu vláken pomocí /CLRTHREADATTRIBUTE nebo tak, že práce s vlákny atribut na funkci bez výchozí položku a pak určete jiné než výchozí vstupní bod s [/Entry](../../build/reference/entry-entry-point-symbol.md) .

Pokud model vláken zadaný ve zdrojovém kódu nesouhlasí s zadaným /CLRTHREADATTRIBUTE modelu vláken, linker se bude ignorovat /CLRTHREADATTRIBUTE a použít model vláken zadaný ve zdrojovém kódu.

Bude nutné k použití jedním – práce s vlákny, například, pokud objekt modelu COM, který používá single-threading je hostitelem vašeho programu CLR.  Pokud vaše CLR program používá více vláken, nelze hostovat objekt modelu COM, který používá single-threading.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **Upřesnit** stránku vlastností.

1. Upravit **atribut vlákna modulu CLR** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)