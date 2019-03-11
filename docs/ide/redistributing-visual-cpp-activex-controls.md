---
title: Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
ms.openlocfilehash: fb4ef7b58f5ef596ac6484761ab891ceb8bb85ad
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744637"
---
# <a name="redistributing-visual-c-activex-controls"></a>Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++

Visual C++ 6.0 poskytuje ovládací prvky ActiveX, které můžete použít v aplikacích, které je pak znovu distribuovat. Tyto ovládací prvky jsou již zahrnuty v jazyce Visual C++. Podle licenční smlouvy pro Visual C++ 6.0 je možné znovu distribuovat tyto ovládací prvky s aplikace vyvinuté v jazyce Visual C++.

> [!NOTE]
>  Visual C++ 6.0 je již nejsou podporovány společností Microsoft.

Seznam distribuovatelné součásti Visual C++ 6.0 ovládacích prvků ActiveX naleznete v tématu Common\Redist\Redist.txt na disku: 1 z disku CD produktu Visual C++ 6.0.

Při distribuci aplikací, musíte nainstalovat a zaregistrovat .ocx ovládacího prvku ActiveX (pomocí Regsvr32.exe). Kromě toho nezapomeňte, že aktuální verze následující systémových souborů (hvězdička znamená, že soubor musí být zaregistrované) má cílový počítač:

- Asycfilt.dll

- Comcat.dll \*

- Oleaut32.dll \*

- Olepro32.dll \*

- Stdole2.tlb

Pokud tyto knihovny DLL nejsou k dispozici v cílovém systému, musíte je aktualizovat pomocí předepsané mechanismus pro aktualizaci odpovídající operační systém. Můžete stáhnout nejnovější aktualizace service Pack pro operační systémy Windows z [ http://windowsupdate.microsoft.com ](http://windowsupdate.microsoft.com).

Při použití ovládacího prvku ActiveX, který se připojuje k databázi, je také potřeba replikovat název zdroje dat na cílovém počítači. Můžete to lze provést prostřednictvím kódu programu pomocí funkce, jako `ConfigDSN`.

Některé distribuovatelné ovládací prvky ActiveX mají další závislosti. Pro každý .ocx soubor v adresáři Os\System na disku CD produktu Visual C++ 6.0 je také .dep soubor. Pro každý soubor .ocx, který chcete znovu distribuovat vyhledejte v odpovídajícím souboru .dep jednu nebo více položek používá. Pokud je uvedený soubor, ujistěte se, že soubor je v cílovém počítači. Všechny knihovny DLL přímo podporuje soubor .ocx musí být zaregistrovaní. (Pro úspěšné Regsvr32.exe, cílový počítač musí nejprve obsahovat všechny knihovny DLL staticky načte ovládacího prvku.) Kromě toho pokud knihovnu DLL, která je uvedena jako závislost také obsahuje soubor .dep v Os\System na disku CD Visual C++ 6.0, musíte také prozkoumat .dep soubor pro použití položky.

## <a name="see-also"></a>Viz také:

[Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)
