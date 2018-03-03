---
title: "pgomgr – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cbb9a4f8b92a1cd495e1312c1aa8a8f77cefcd3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="pgomgr"></a>pgomgr
Přidá data profilu z jednoho nebo více souborů .pgc .pgd souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
pgomgr [options] pgcfiles pgdfile  
```  
  
#### <a name="parameters"></a>Parametry  
 `options`  
 K pgomgr – lze zadat následující možnosti:  
  
 **/ help –**zobrazí dostupná pgomgr – možnosti (zkratka pro /?).  
  
 **/ clear –**způsobí, že soubor .pgd vymazat všechny informace o profilu. Nelze zadat .pgc souboru, když **/clear** je zadán.  
  
 **/ podrobností**– zobrazuje podrobné statistiky, včetně toku grafu pokrytí informací.  
  
 **/ souhrnné**– zobrazí za – funkce statistiky.  
  
 **/ Jedinečný**– při použití s **nebo souhrnných**, příčiny dekorované názvy funkcí pro zobrazení.  Výchozí nastavení, když je jedinečný nepoužívá, je pro názvy bez upraveného funkce, který se má zobrazit.  
  
 **/ merge**[**:***n*]**–**způsobí, že data v .pgc soubor nebo soubory, které mají být přidány do souboru .pgd.  Volitelný parametr  *n* , umožňují určit hat data musí být přidaní  *n*  časy.  Například pokud scénář běžně provádějí 6krát, můžete to provést jednou spustit test a přidat jej do souboru .pgd šestkrát s **pgomgr – /merge:6**.  
  
 `pgcfiles`  
 .Pgc jeden nebo více souborů, jejichž data profilu můžete sloučit do souboru .pgd. Můžete zadat soubor .pgc jeden nebo více souborů .pgc. Pokud nezadáte žádné soubory .pgc, bude pgomgr – slučte všechny soubory .pgc, jejichž názvy souborů jsou stejné jako soubor .pgd.  
  
 `pgdfile`  
 .Pgd soubor, do kterého jsou slučování dat z .pgc soubor či soubory.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Můžete spustit tento nástroj pouze z [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] příkazového řádku. Nelze ji spustit z příkazového řádku systému nebo v Průzkumníku souborů.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu byl vymazán soubor .pgd dat profilu.  
  
```  
pgomgr /clear myapp.pgd  
```  
  
 V následujícím příkladu se data profilu v myapp1.pgc přidal do souboru .pgd 3krát.  
  
```  
pgomgr /merge:3 myapp1.pgc myapp.pgd  
```  
  
 V následujícím příkladu se data profilu z všechny soubory # .pgc Moje aplikace přidá do souboru myapp.pgd.  
  
```  
pgomgr -merge myapp1.pgd  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje pro ruční optimalizace na základě profilu](../../build/reference/tools-for-manual-profile-guided-optimization.md)