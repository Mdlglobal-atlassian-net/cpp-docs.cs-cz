---
title: Chyba sestavení projektu PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: ec2490bad70d2b2eb72cbb48771900f09f8c2f67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226488"
---
# <a name="project-build-error-prj0050"></a>Chyba sestavení projektu PRJ0050

Registrace výstupu se nezdařila. Ujistěte se prosím, že máte příslušná oprávnění k úpravám registru.

Systém sestavení Visual C++ nebyl schopen registrovat výstup sestavení (knihovna dll nebo .exe). Musíte být přihlášeni jako správce k úpravám registru.

Pokud vytváříte soubor .dll, můžete se pokusit zaregistrovat ručně pomocí regsvr32.exe soubor .dll, mělo by se zobrazit informace o sestavení o příčině selhání.

Pokud vytváříte nejsou ve formátu .dll, podívejte se na příkaz, který způsobí chybu v protokolu sestavení.