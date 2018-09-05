---
title: DCOMCNFG | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- DCOMCNFG
dev_langs:
- C++
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46a395759322651aee75541ff0b121b608b9e74d
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765275"
---
# <a name="dcomcnfg"></a>DCOMCNFG

DCOMCNFG je nástroj Windows NT 4.0, který chcete nakonfigurovat různá nastavení specifická pro model DCOM v registru. V okně DCOMCNFG má tři stránky: výchozí zabezpečení, výchozí vlastnosti a aplikací. V části Windows 2000 čtvrtá stránka výchozí protokolů je k dispozici.

## <a name="default-security-page"></a>Výchozí stránka zabezpečení

Na stránce zabezpečení můžete použít k určení výchozích oprávnění pro objekty v systému. Výchozí zabezpečení stránka má tři části: přístup, spuštění a konfigurace. Chcete-li změnit výchozí hodnoty pro oddíl, klikněte na odpovídající **upravit výchozí nastavení** tlačítko. Tato nastavení výchozí zabezpečení jsou uložena v registru pod `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.

## <a name="default-protocols-page"></a>Výchozí stránka protokoly

Tato stránka obsahuje sadu síťových protokolů, které jsou k dispozici DCOM v tomto počítači. Odpovídá pořadí priority, v němž budou používána; první v seznamu má nejvyšší prioritu. Protokoly můžete přidat nebo odstranit z této stránky.

## <a name="default-properties-page"></a>Výchozí stránka Vlastnosti

Na stránce výchozí vlastnosti. je nutné vybrat **povolit používání objektů DCOM v tomto počítači** zaškrtávací políčko, pokud chcete, aby klienti na jiné počítače pro přístup COM objekty, které běží na tomto počítači. Výběr, tato možnost nastaví `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` hodnota, která se `Y`.

## <a name="applications-page"></a>Stránka aplikace

Můžete změnit nastavení pro daný objekt se stránkou aplikací. Jednoduše vyberte aplikaci ze seznamu a klikněte na tlačítko **vlastnosti** tlačítko. V okně vlastnosti má pět stránky:

- Obecná stránka potvrdí aplikace, kterou pracujete.

- Stránka umístění vám umožňuje určit, kde by měla spustit aplikace, když klient volá `CoCreateInstance` na relevantní identifikátoru CLSID. Pokud vyberete **spouštět aplikace na následujícím počítači** zaškrtněte políčko a zadejte název počítače, o `RemoteServerName` hodnota se přidá do části AppID pro danou aplikaci. Vymazání **spuštění aplikace na tomto počítači** přejmenování zaškrtávacího políčka `LocalService` hodnota, která se `_LocalService` a tím, zakáže.

- Na stránce zabezpečení je podobná stránka výchozí zabezpečení najdete v okně DCOMCNFG s tím rozdílem, že tato nastavení platí pouze pro aktuální aplikaci. Znovu jsou nastavení uložena v ID aplikace pro daný objekt.

- Stránka identifikace identifikuje, u kterého uživatele se používá ke spuštění aplikace.

- Na stránce koncové body zobrazí sadu koncových bodů, které jsou k dispozici pro klienty vybraného serveru DCOM a protokoly.

## <a name="see-also"></a>Viz také

[Služby](../atl/atl-services.md)

