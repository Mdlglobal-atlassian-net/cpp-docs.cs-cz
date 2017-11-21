---
title: __fastfail | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f7a9fe4f4a70f55061addab05f90bda389fd8949
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fastfail"></a>__fastfail
**Konkrétní Microsoft**  
  
 Okamžitě ukončí proces volání s minimální režie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __fastfail(unsigned int code);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`code`  
 A `FAST_FAIL_<description>` symbolický konstanta ze souboru winnt.h nebo wdm.h, která určuje důvod ukončení procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 `__fastfail` Vnitřní nevrátí.  
  
## <a name="remarks"></a>Poznámky  
 `__fastfail` Vnitřní poskytuje mechanismus pro *rychlý selhání* žádost – způsob, jak potenciálně poškozená proces k žádosti o okamžitou proces dokončen. Kritické chyby, které mohou mít zásobníku nad rámec obnovení a stavu program poškozených nelze zpracovat pomocí regulárních zpracování budovy výjimek. Použití `__fastfail` ukončit proces pomocí minimální režie.  
  
 Interně `__fastfail` je implementována pomocí několik mechanismů specifické pro architekturu:  
  
|Architektura|Instrukce|Umístění argumentu kódu|  
|------------------|-----------------|-------------------------------|  
|x86|int 0x29|ecx|  
|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|int 0x29|RCX|  
|ARM|Operační kód 0xDEFB|r0|  
  
 Žádost o rychlé selhání je samostatný a obvykle vyžaduje právě dva pokyny k provedení. Jakmile požadavek rychlé selhání byl proveden jádra pak provede příslušnou akci. V uživatelském režimu kódu neexistují žádné závislosti paměti nad rámec samotné ukazatel instrukce při rychlé selhání událost se vyvolá. To maximalizuje jeho spolehlivost i v případě, že se jedná o poškození závažné paměti.  
  
 `code` Argument – jeden z `FAST_FAIL_<description>` symbolický konstanty ze souboru winnt.h nebo wdm.h—describes typ stavu selhání a je součástí sestavy selhání způsobem konkrétní prostředí.  
  
 Požadavky rychlého selhání uživatelského režimu se zobrazí jako druhý prvního výjimce bez s kód výjimky 0xC0000409 a parametr alespoň jednu výjimku. První parametr výjimky je `code` hodnotu. Tento kód výjimky označuje (zasílání chyb k systému Windows) a ladění infrastruktury, že proces je poškozený a že minimální akce v rámci procesu by měla být provedena v reakci na selhání. Požadavky rychlého selhání režimu jádra jsou implementované pomocí vyhrazené kontroly chyb kódu, `KERNEL_SECURITY_CHECK_FAILURE` (0x139). V obou případech jsou žádné obslužné rutiny výjimek vyvolat, protože program musí být v poškozeném stavu. Pokud se nachází ladicí program, se má možnost pro zjištění stavu aplikace před ukončení.  
  
 Podpora pro nativní rychlé selhání mechanismus začal ve Windows 8. Operační systémy Windows, které nativně nepodporují pokyn rychlé selhání bude obvykle považovat žádost rychlá selhání za porušení pravidel přístupu nebo `UNEXPECTED_KERNEL_MODE_TRAP` kontroly chyb. V těchto případech je program stále ukončenou, ale nemusí nutně prokázat jako rychle.  
  
 `__fastfail`je k dispozici pouze jako vnitřní.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__fastfail`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], ARM|  
  
 **Soubor hlaviček** \<intrin.h >  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)