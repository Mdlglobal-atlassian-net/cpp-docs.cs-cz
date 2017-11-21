---
title: "Redistribuování aplikace ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e5a91ffb267d413c980d2313efbf9b0c41c0932
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="redistributing-an-atl-application"></a>Redistribuování aplikace ATL
Spouštění v sadě Visual Studio 2012, Active Template Library (ATL) je knihovna pouze záhlaví. Projekty knihovny ATL nemají dynamické propojení do knihovny ATL možnost. Vyžaduje se žádné redistributable knihovna ATL.  
  
 Pokud provedete opětovnou distribuci aplikace knihovny ATL spustitelný soubor, je nutné zaregistrovat soubor .exe (a všechny ovládací prvky je uvnitř) po vydání následujícího příkazu:  
  
```  
filename /regserver  
```  
  
 kde `filename` je název spustitelného souboru.  
  
 V sadě Visual Studio 2010 se dají vytvářet projektu knihovny ATL pro MinDependency nebo MinSize konfigurace. Konfigurace MinDependency je co získáte, když nastavíte **použití knihovny ATL** vlastnost **statické propojení knihovny ATL** na **Obecné** stránku vlastností a sadu  **Knihovna runtime** vlastnost **Vícevláknová (nebo MT)** na **generování kódu** stránka vlastností (složka C/C++).  
  
 Konfigurace MinSize je co získáte, když nastavíte **použití knihovny ATL** vlastnost **dynamického propojení knihovny ATL** na **Obecné** stránka vlastností, nebo sady **modulu Runtime Knihovna** vlastnost, která má **Multi-threaded DLL (/ MD)** na **generování kódu** stránka vlastností (C/C++ složka).  
  
 MinSize dělá výstupní soubor jako malý, jak je možné, ale vyžaduje, aby knihovny ATL100.dll a Msvcr100.dll (Pokud jste vybrali **Multi-threaded DLL (/ MD)** možnost) jsou na cílovém počítači. Knihovna ATL100.dll by měl zaregistrovaná na cílový počítač a ujistěte se, zda je k dispozici všechny funkce ATL. Knihovna ATL100.dll obsahuje ANSI a exportuje kódování Unicode.  
  
 Pokud vytvoříte projekt knihovny ATL nebo šablony technologie OLE DB pro cílový MinDependency, není nutné instalovat a registrovat knihovnu ATL100.dll na cílovém počítači, i když může získat větší bitové kopie programu.  
  
 Pokud provedete opětovnou distribuci aplikace knihovny ATL spustitelný soubor, je nutné zaregistrovat soubor .exe (a všechny ovládací prvky je uvnitř) po vydání následujícího příkazu:  
  
```  
filename /regserver  
```  
  
 kde `filename` je název spustitelného souboru.  
  
 Pro aplikace, šablony technologie OLE DB zajistěte, aby cílový počítač nejnovější verze Microsoft Data Access Components (MDAC) soubory. Další informace najdete v tématu [Redistribuce pomocných souborů databáze](../ide/redistributing-database-support-files.md).  
  
## <a name="see-also"></a>Viz také  
 [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md)