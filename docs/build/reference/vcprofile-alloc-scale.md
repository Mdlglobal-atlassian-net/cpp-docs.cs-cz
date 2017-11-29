---
title: "VCPROFILE_ALLOC_SCALE – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VCPROFILE_ALLOC_SCALE
dev_langs: C++
helpviewer_keywords: VCPROFILE_ALLOC_SCALE environment variable
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed767299778b65a7275bbfd225daaf46ec0e98be
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE
Upravte množství paměti přidělené pro všechna data profilu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### <a name="parameters"></a>Parametry  
 `scale_value`  
 Škálování hodnotu pro velikost paměti, kterou chcete použít pro spuštění scénáře testování.  Výchozí hodnota je 1.  
  
## <a name="remarks"></a>Poznámky  
 Ve výjimečných případech, nebude dostatek paměti k dispozici pro podporu shromažďování dat profilu při spouštění testovací scénáře.  V takových případech můžete zvýšit množství paměti s `VCPROFILE_ALLOC_SCALE`.  
  
 Pokud se zobrazí chybová zpráva během spustit test, který označuje, zda máte dostatek paměti, přiřadit hodnotu větší na `VCPROFILE_ALLOC_SCALE`, dokud se test spustí dokončeno bez chyb z důvodu nedostatku paměti.  
  
## <a name="example"></a>Příklad  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## <a name="see-also"></a>Viz také  
 [Proměnné prostředí pro optimalizace na základě profilu](../../build/reference/environment-variables-for-profile-guided-optimizations.md)