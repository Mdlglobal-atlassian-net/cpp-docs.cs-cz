---
title: DCOMCNFG | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DCOMCNFG
dev_langs:
- C++
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f40b372666ba2b623450eb0e58a6c0ff372559ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dcomcnfg"></a>DCOMCNFG
**DCOMCNFG** je nástroj Windows NT 4.0, který umožňuje nakonfigurovat různá nastavení pro konkrétní DCOM v registru. **DCOMCNFG** okno má tři stránky: výchozí zabezpečení, výchozí vlastnosti a aplikace. V systému Windows 2000 na čtvrté stránce Výchozí protokoly nachází.  
  
## <a name="default-security-page"></a>Výchozí stránka zabezpečení  
 Stránka zabezpečení výchozí můžete nastavit výchozí oprávnění pro objekty v systému. Stránka výchozí zabezpečení má tři části: přístup, spuštění a konfigurace. Chcete-li změnit výchozí hodnoty pro oddíl, klikněte na odpovídající **upravit výchozí nastavení** tlačítko. Tato nastavení výchozí zabezpečení jsou uložené v registru v části `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.  
  
## <a name="default-protocols-page"></a>Výchozí stránka protokoly  
 Tato stránka obsahuje sadu síťových protokolů, které jsou k dispozici pro DCOM v tomto počítači. Určuje pořadí priority ve kterém se má používat; první v seznamu má nejvyšší prioritu. Protokoly můžete přidat nebo odstranit z této stránky.  
  
## <a name="default-properties-page"></a>Výchozí vlastnosti stránky  
 Na stránce výchozí vlastnosti. je nutné vybrat **povolit používání objektů DCOM v tomto počítači** zaškrtávací políčko, pokud chcete, aby klienti na jiné počítače pro přístup COM objekty v tomto počítači spuštěna. Výběrem této možnosti se nastaví `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` hodnotu `Y`.  
  
## <a name="applications-page"></a>Stránka aplikace  
 Můžete změnit nastavení pro konkrétní objekt s stránku aplikací. Stačí vybrat aplikaci ze seznamu a klikněte **vlastnosti** tlačítko. Okno vlastností má pět stránky:  
  
-   Stránku Obecné potvrdí aplikaci, kterou pracujete.  
  
-   Na stránce umístění můžete zadat, kde by měla spustit aplikace, když klient zavolá `CoCreateInstance` na příslušné CLSID. Pokud jste vybrali **spuštění aplikace na jiný počítač** zaškrtněte políčko a zadejte název počítače, pak `RemoteServerName` hodnota se přidá pod AppID pro příslušnou aplikaci. Vymazání **spuštění aplikace v tomto počítači** políčko přejmenuje `LocalService` hodnotu `_LocalService` a tím, zakáže ho.  
  
-   Stránka zabezpečení je podobná zabezpečení výchozí stránka nalezena v **DCOMCNFG** okně s tím rozdílem, že toto nastavení platí pouze pro aktuální aplikaci. Znovu tato nastavení uložena v ID aplikace pro daný objekt.  
  
-   Stránka identifikace identifikuje, které uživatel slouží ke spuštění aplikace.  
  
-   Na stránce koncové body zobrazí sadu protokoly a koncové body k dispozici pro klienty vybraného serveru DCOM.  
  
## <a name="see-also"></a>Viz také  
 [Služby](../atl/atl-services.md)

