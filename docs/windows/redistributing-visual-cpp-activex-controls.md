---
title: Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: 4c7806502024789ed41f3043d7db6c87c7c71ee3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359871"
---
# <a name="redistributing-visual-c-activex-controls"></a>Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++

Visual C++ 6.0 poskytuje ovládací prvky ActiveX, které můžete použít v aplikacích, které pak redistribuujete. Tyto ovládací prvky již nejsou součástí visual c++. Podle licenčních smluv pro Visual C++ 6.0 můžete tyto ovládací prvky dále distribuovat s aplikacemi vyvinutými v jazyce Visual C++.

> [!NOTE]
> Visual C++ 6.0 již není podporován společností Microsoft.

Seznam redistribuovatelných ovládacích prvků ActiveX jazyka Visual C++ 6.0 naleznete v tématu Common\Redist\Redist.txt na disku 1 disku CD-ROM produktu Visual C++ 6.0.

Při distribuci aplikací je nutné nainstalovat a zaregistrovat soubor .ocx pro ovládací prvek ActiveX (pomocí programu Regsvr32.exe). Kromě toho byste se měli ujistit, že cílový počítač má aktuální verze následujících systémových souborů (hvězdička označuje, že soubor musí být registrován):

- Asycfilt.dll

- Comcat.dll\*

- Oleaut32.dll\*

- Olepro32.dll\*

- Stdole2.tlb

Pokud tyto knihovny DLL nejsou k dispozici v cílovém systému, je třeba je aktualizovat pomocí předepsaného mechanismu pro aktualizaci odpovídajícího operačního systému. Nejnovější aktualizace Service Pack pro operační systémy [http://windowsupdate.microsoft.com](https://windowsupdate.microsoft.com)Windows si můžete stáhnout z aplikace .

Při použití ovládacího prvku ActiveX, který se připojuje k databázi, je také nutné replikovat název zdroje dat v cílovém počítači. Můžete to provést programově s `ConfigDSN`funkcemi, jako je například .

Některé redistribuovatelné ovládací prvky ActiveX mají další závislosti. Pro každý soubor OCX ve složce Os\System na disku CD-ROM produktu Visual C++ 6.0 existuje také soubor DEP. U každého souboru OCX, který chcete znovu distribuovat, vyhledejte jednu nebo více položek USES v odpovídajícím souboru DEP. Pokud je soubor uveden, je nutné zajistit, aby byl soubor v cílovém počítači. Všechny knihovny DLL, které přímo podporují soubor OCX, musí být registrovány. (Aby byl program Regsvr32.exe úspěšný, musí cílový počítač nejprve obsahovat všechny knihovny DLL, které ovládací prvek staticky načte.) Kromě toho pokud dll, který je uveden jako závislost má také soubor .dep ve složce OS\System na cd Visual C++ 6.0, musíte také prozkoumat, že soubor .DEP pro položky USES.

## <a name="see-also"></a>Viz také

[Redistribuce souborů Visual C++](redistributing-visual-cpp-files.md)
