---
title: Chyba sestavení projektu PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: ada89b074fd8e0c2bfc75ba833e9c5966a145312
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616863"
---
# <a name="project-build-error-prj0016"></a>Chyba sestavení projektu PRJ0016

Nastavení zabezpečení uživatele zabránit procesu vytváření. Tato nastavení pro sestavování jsou vyžadována.

Jste přihlášeni jako uživatel, který nemá oprávnění k vytváření procesů pomocí procesu. Musíte změnit úrovně oprávnění pro tento uživatelský účet nebo kontaktujte správce účtu.

K této chybě může dojít, pokud nastavte následující klíč registru:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Chcete-li tuto chybu vyřešit, odstraňte klíč RestrictRun. Pokud tento klíč registru je potřeba, připojte **vcspawn.exe** do seznamu položek v klíči.

Další příčinou této chyby je, že vaše nastavení zásad nezahrnuje VCSpawn.exe v klíči registru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako Povolené program okno pro tento uživatelský účet.

Další informace najdete v tématu [týkajícími se nastavení zásad systému](https://msdn.microsoft.com/library/aa372139), v části "Spouštět pouze povolené aplikace Windows".