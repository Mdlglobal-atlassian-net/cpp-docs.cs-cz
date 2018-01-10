---
title: "Redistribuce ovládacích prvků ActiveX jazyka Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [C++], redistributing
- controls [C++], distributing
ms.assetid: eefbb7e4-d28c-4c35-98bf-d9540cfaae83
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c520d365a259c36baab8edeb9049aab9ac89925a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-visual-c-activex-controls"></a>Redistribuce souborů ovládacích prvků ActiveX jazyka Visual C++
Visual C++ verze 6.0 poskytuje ovládací prvky ActiveX, které můžete použít v aplikacích, které pak znovu distribuovat. Tyto ovládací prvky jsou již zahrnuty v jazyce Visual C++. Podle licenční smlouvy pro Visual C++ verze 6.0 je možné znovu distribuovat tyto ovládací prvky s aplikace vyvinuté v jazyce Visual C++.  
  
> [!NOTE]
>  Visual C++ verze 6.0 je podporován společností Microsoft.  
  
 Seznam distribuovatelné ovládací prvky ActiveX jazyka Visual C++ 6.0 naleznete v Common\Redist\Redist.txt na disk 1 z disku CD produktu Visual C++ verze 6.0.  
  
 Při distribuci aplikací, je nutné nainstalovat a zaregistrovat .ocx pro ovládací prvek ActiveX (s použitím Regsvr32.exe). Kromě toho můžete Ujistěte se, že cílový počítač má aktuální verze následujících systému souborů (hvězdička označuje, že soubor musí být zaregistrovaný):  
  
-   Asycfilt.dll  
  
-   Comcat.dll *  
  
-   Oleaut32.dll *  
  
-   Olepro32.dll *  
  
-   Stdole2.tlb  
  
 Pokud tyto knihovny DLL nejsou k dispozici v cílovém systému, budete muset získat jejich aktualizaci pomocí předepsaných mechanismus pro aktualizaci odpovídající operační systém. Můžete si stáhnout nejnovější aktualizace service Pack pro operační systémy Windows z [http://windowsupdate.microsoft.com](http://windowsupdate.microsoft.com).  
  
 Pokud vaše aplikace používá jednu z ovládacích prvků ActiveX, které připojuje k databázi, musíte mít Microsoft Data Access Components (MDAC) nainstalované v cílovém systému. Další informace najdete v tématu [Redistribuce pomocných souborů databáze](../ide/redistributing-database-support-files.md).  
  
 Při použití ovládacího prvku ActiveX, který se připojuje k databázi, budete také muset replikovat název zdroje dat na cílovém počítači. To provedete prostřednictvím kódu programu s funkcemi, jako například `ConfigDSN`.  
  
 Některé distribuovatelné ovládací prvky ActiveX mají další závislosti. Pro každý .ocx soubor v adresáři Os\System na disku CD produktu Visual C++ verze 6.0 existuje také .dep soubor. Pro každý soubor .ocx, který chcete znovu distribuovat vyhledejte jeden nebo více položek používá v odpovídajícím .dep souboru. Pokud soubor je uveden, je třeba zkontrolovat, zda je soubor v cílovém počítači. Všechny knihovny DLL podporující přímo soubor .ocx musí být registrované. (Pro úspěšné Regsvr32.exe, cílový počítač musí napřed obsahovat všechny knihovny DLL staticky načte ovládacího prvku.) Kromě toho pokud knihovny DLL, která je uvedena jako závislost má také .dep soubor v adresáři Os\System na disku CD Visual C++ verze 6.0, musíte také prozkoumat .dep soubor pro položky používá.  
  
## <a name="see-also"></a>Viz také  
 [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)