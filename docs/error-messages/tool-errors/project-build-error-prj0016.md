---
title: Chyba sestavení projektu PRJ0016
ms.date: 11/04/2016
f1_keywords:
- PRJ0016
helpviewer_keywords:
- PRJ0016
ms.assetid: e9745336-883a-4c70-9c40-7753e02f0325
ms.openlocfilehash: 6733ef1f390f2ff377356dda3f7cd3ebfe10cc2b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509882"
---
# <a name="project-build-error-prj0016"></a>Chyba sestavení projektu PRJ0016

Nastavení zabezpečení uživatele brání procesu v jeho vytvoření. Tato nastavení se vyžadují pro sestavování.

Jste přihlášeni jako uživatel, který nemá oprávnění k vytváření procesů pomocí procesu. Musíte změnit úrovně oprávnění pro tento uživatelský účet, nebo se obraťte na správce účtu.

K této chybě může dojít také v případě, že je nastaven následující klíč registru:

\\\HKCU\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\RestrictRun

Tuto chybu můžete vyřešit tak, že odstraníte klíč RestrictRun. Pokud je tento klíč registru potřeba, přidejte **VCSpawn. exe** do seznamu položek v klíči.

Další příčinou této chyby je, že nastavení zásad nezahrnuje VCSpawn. exe do klíče registru HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\RestrictRun jako povolený program pro tento uživatelský účet.

Další informace najdete v tématu [dodržování nastavení systémových zásad](/previous-versions/windows/desktop/Policy/adhering-to-system-policy-settings)v části "spouštění pouze povolených aplikací systému Windows".