---
title: Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc319c2da652cd1c43f23c13456b32f978595199
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207954"
---
# <a name="redistributing-visual-c-activex-controls"></a>Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++
Visual C++ 6.0 poskytuje ovládací prvky ActiveX, které můžete použít v aplikacích, které je pak znovu distribuovat. Tyto ovládací prvky jsou již zahrnuty v jazyce Visual C++. Podle licenční smlouvy pro Visual C++ 6.0 je možné znovu distribuovat tyto ovládací prvky s aplikace vyvinuté v jazyce Visual C++.  
  
> [!NOTE]
>  Visual C++ 6.0 je již nejsou podporovány společností Microsoft.  
  
 Seznam distribuovatelné součásti Visual C++ 6.0 ovládacích prvků ActiveX naleznete v tématu Common\Redist\Redist.txt na disku: 1 z disku CD produktu Visual C++ 6.0.  
  
 Při distribuci aplikací, musíte nainstalovat a zaregistrovat .ocx ovládacího prvku ActiveX (pomocí Regsvr32.exe). Kromě toho nezapomeňte, že aktuální verze následující systémových souborů (hvězdička znamená, že soubor musí být zaregistrované) má cílový počítač:  
  
-   Asycfilt.dll  
  
-   Comcat.dll \*  
  
-   Oleaut32.dll \*  
  
-   Olepro32.dll \*  
  
-   Stdole2.tlb  
  
 Pokud tyto knihovny DLL nejsou k dispozici v cílovém systému, musíte je aktualizovat pomocí předepsané mechanismus pro aktualizaci odpovídající operační systém. Můžete stáhnout nejnovější aktualizace service Pack pro operační systémy Windows z [ http://windowsupdate.microsoft.com ](http://windowsupdate.microsoft.com).  
  
 Pokud vaše aplikace používá jednu z ovládací prvky ActiveX, které se připojí k databázi, musíte mít Microsoft Data Access Components (MDAC) nainstalované v cílovém systému. Další informace najdete v tématu [Redistribuce pomocných souborů databáze](../ide/redistributing-database-support-files.md).  
  
 Při použití ovládacího prvku ActiveX, který se připojuje k databázi, je také potřeba replikovat název zdroje dat na cílovém počítači. Můžete to lze provést prostřednictvím kódu programu pomocí funkce, jako `ConfigDSN`.  
  
 Některé distribuovatelné ovládací prvky ActiveX mají další závislosti. Pro každý .ocx soubor v adresáři Os\System na disku CD produktu Visual C++ 6.0 je také .dep soubor. Pro každý soubor .ocx, který chcete znovu distribuovat vyhledejte v odpovídajícím souboru .dep jednu nebo více položek používá. Pokud je uvedený soubor, ujistěte se, že soubor je v cílovém počítači. Všechny knihovny DLL přímo podporuje soubor .ocx musí být zaregistrovaní. (Pro úspěšné Regsvr32.exe, cílový počítač musí nejprve obsahovat všechny knihovny DLL staticky načte ovládacího prvku.) Kromě toho pokud knihovnu DLL, která je uvedena jako závislost také obsahuje soubor .dep v Os\System na disku CD Visual C++ 6.0, musíte také prozkoumat .dep soubor pro použití položky.  
  
## <a name="see-also"></a>Viz také  
 [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)