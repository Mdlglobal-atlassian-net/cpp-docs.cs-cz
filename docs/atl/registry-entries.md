---
title: Položky registru (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- registry, ATL services entries
- registry, application IDs
ms.assetid: 881989b7-61bb-459a-a13e-3bfcb33e184e
ms.openlocfilehash: b61aae9ba9316dded1dcb11353e52eb2fffd49a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472875"
---
# <a name="registry-entries"></a>Položky registru

Model DCOM představil nový koncept ID aplikace (AppID), které skupiny možnosti konfigurace pro jeden nebo více objektů DCOM do centralizovaného umístění v registru. AppID určíte tak, že její hodnota v AppID se pojmenovaná hodnota pod CLSID objektu.

Ve výchozím nastavení používá službu generované ATL jeho identifikátor CLSID jako identifikátor GUID pro své ID aplikace. V části `HKEY_CLASSES_ROOT\AppID`, můžete zadat položky specifické pro model DCOM. Na začátku existují dvě položky:

- `LocalService`, s hodnotou stejný jako název služby. Pokud tato hodnota existuje, používá se místo `LocalServer32` klíč CLSID.

- `ServiceParameters`, s hodnotou rovná `-Service`. Tato hodnota určuje parametry, které se předávají služby při spuštění. Všimněte si, že tyto parametry jsou předány služby `ServiceMain` funkce se `WinMain`.

Jakékoli DCOM služby také musí vytvořit jiný klíč v rámci `HKEY_CLASSES_ROOT\AppID`. Tento klíč je stejný jako název souboru EXE a funguje jako křížový odkaz, protože obsahuje hodnotu AppID přejdete zpět AppID položky.

## <a name="see-also"></a>Viz také

[Služby](../atl/atl-services.md)

