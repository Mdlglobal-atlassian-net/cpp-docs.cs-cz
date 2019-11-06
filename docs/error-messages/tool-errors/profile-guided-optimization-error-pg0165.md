---
title: PG0165 chyba optimalizace na základě profilu
description: Popisuje chyby PG0165 při čtení dat PGO (profil-řízená optimalizace).
ms.date: 10/30/2019
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: c5e5c5d37f8c70a6c2a3d9f7a43c13bb46d0e25a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626805"
---
# <a name="profile-guided-optimization-error-pg0165"></a>PG0165 chyba optimalizace na základě profilu

Při čtení dat optimalizace s asistencí na základě profilu došlo k chybě. Tato chyba se může objevit v několika formách:

> Čte se*filename. pgd*: verze souboru PGD se nepodporuje (Neshoda verzí).

Soubory PGD jsou specifické pro konkrétní sadu nástrojů kompilátoru. Tato chyba je generována, pokud používáte jiný kompilátor než ten, který byl použit k vytvoření *souboru filename. pgd*. Tato chyba označuje, že sada nástrojů kompilátoru nemůže k optimalizaci aktuálního programu použít data z *souboru filename. pgd* . Chcete-li tento problém vyřešit, obnovte *soubor filename*. pgd pomocí aktuální sady nástrojů kompilátoru.

> Probíhá čtení*souboru filename. pgd*: soubor PGD je jen pro čtení.

Tato chyba se zobrazí, pokud je soubor PGD v systému souborů označen jen pro čtení. Chcete-li tento problém vyřešit, změňte atributy souboru na čtení i zápis.
