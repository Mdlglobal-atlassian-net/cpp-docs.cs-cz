---
title: "pgosweep – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c703bc68a36dd21c837e62738d9d2c2631502a0d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pgosweep"></a>pgosweep
Používá se v optimalizace na základě profilu zapsat všechna data profilu z spuštěným programem do souboru .pgc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
pgosweep [options] image pgcfile  
```  
  
#### <a name="parameters"></a>Parametry  
 `options`  
 Volitelný parametr, který může být ponecháno prázdné. Platné hodnoty pro `options` jsou následující:  
  
-   **/?** nebo **/help,** zobrazí zprávu nápovědy.  
  
-   **/noreset,** zachovává počet v modulu runtime datové struktury.  
  
 `image`  
 Úplná cesta souboru .exe nebo .dll, který byl vytvořen pomocí /LTCG:PGINSTRUMENT – možnost kompilátoru.  
  
 `pgcfile`  
 Soubor .pgc, kde tento příkaz se zapsat data počty.  
  
## <a name="remarks"></a>Poznámky  
 Tento příkaz lze použít na programy, které byly vytvořené s možností kompilátoru /LTCG:PGINSTRUMENT. To přerušení spuštěným programem a zapisuje data profilu do nového souboru .pgc. Ve výchozím nastavení příkaz obnoví počty po každé operaci zápisu. Pokud zadáte **/noreset** možnost příkaz záznam hodnoty, ale neprovádí vynulování je v běžící aplikaci. Tato možnost vám poskytne duplicitních dat. Pokud načíst data profilu později.  
  
 Alternativní použití pro `pgosweep` je načíst informace o profilu jenom pro modul runtime aplikace. Například můžete spustit `pgosweep` krátce po spuštění aplikace a zahodit tento soubor. To by odeberte profil data související s náklady na spuštění. Potom můžete spustit `pgosweep` před ukončením aplikace. Shromážděná data má teď informace o profilu pouze z modulu runtime.  
  
 Když zadáte název souboru .pgc (`pgcfile`) můžete použít ve standardním formátu, který je *appname! n*.pgc. Pokud použijete tento formát, kompilátor zjistí tato data ve fázi /LTCG:PGO. Pokud použijete ve standardním formátu, musíte použít [pgomgr –](../../build/reference/pgomgr.md) sloučit .pgc soubory.  
  
## <a name="example"></a>Příklad  
  
```  
pgosweep myapp.exe myapp!1.pgc  
```  
  
 V tomto příkladu `pgosweep` zapíše aktuální informace o profilu pro myapp.exe myapp!1.pgc.  
  
## <a name="see-also"></a>Viz také  
 [Nástroje pro ruční optimalizace na základě profilu](../../build/reference/tools-for-manual-profile-guided-optimization.md)