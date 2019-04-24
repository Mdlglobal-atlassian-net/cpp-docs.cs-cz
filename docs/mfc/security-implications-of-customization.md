---
title: Vliv přizpůsobení na zabezpečení
ms.date: 11/04/2016
helpviewer_keywords:
- security, MFC Feature Pack
- MFC Feature Pack, security
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
ms.openlocfilehash: 9164983a6634e069195f3498bea56b595a2a2381
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308469"
---
# <a name="security-implications-of-customization"></a>Vliv přizpůsobení na zabezpečení

Toto téma popisuje potenciální slabá místa zabezpečení v knihovně MFC.

## <a name="potential-security-weakness"></a>Potenciální slabá místa zabezpečení

MFC umožňuje uživateli upravit vzhled uživatelského rozhraní, například vzhled tlačítek a ikony. Knihovna MFC také podporuje uživatelem definované nástroje, které umožní uživateli spustit příkazy prostředí. Ohrožení zabezpečení mohou nastat, protože vlastní nastavení aplikace se ukládají do profilu uživatele v registru. Každý, kdo má přístup k registru můžete upravit tato nastavení a změnit vzhled aplikace a chování. Například může správce v počítači zosobnit uživatele tak, že uživatele aplikace pro spuštění libovolné aplikace (i ze síťové sdílené složky).

## <a name="workarounds"></a>Alternativní řešení

Doporučujeme, abyste kterýmkoli z těchto tří způsobů zavřete slabá místa v registru:

- Šifrování dat, která je uložena existuje

- Data Store v zabezpečené souboru místo v registru.

   Chcete-li provést některý z těchto prvních dvou způsobů, odvoďte třídu z [csettingsstore – třída](../mfc/reference/csettingsstore-class.md) a přepsat její metody k implementaci šifrování nebo úložiště mimo registru.

- Můžete také zakázat přizpůsobení v aplikaci.

## <a name="see-also"></a>Viz také:

[Přizpůsobení pro prostředí MFC](../mfc/customization-for-mfc.md)
