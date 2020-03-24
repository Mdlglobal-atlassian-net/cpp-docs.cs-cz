---
title: Závažná chyba C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: 10a411dfc942498a98959d9a23cb42dfb93cf2ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202823"
---
# <a name="fatal-error-c1902"></a>Závažná chyba C1902

Neshoda správce databáze programu; Zkontrolujte prosím instalaci.

Soubor databáze programu (PDB) byl vytvořen pomocí novější verze mspdb*xxx*. dll, než je ten, který byl nalezen ve vašem systému. Tato chyba obvykle znamená, že Mspdbsrv. exe nebo mspdbcore. dll chybí nebo mají jiné verze než mspdb*xxx*. dll. (Zástupný symbol *xxx* v názvu souboru mspdb*xxx*. dll se mění podle verze produktu. Například v aplikaci Visual Studio 2015 je název souboru mspdb140. dll.)

Zajistěte, aby byly v systému nainstalovány vyhovující verze souborů Mspdbsrv. exe, mspdbcore. dll a mspdb*xxx*. dll. Ujistěte se, že neodpovídající verze nebyly zkopírovány do adresáře, který obsahuje nástroje pro kompilátor a propojování pro vaši cílovou platformu. Mohli jste například zkopírovat soubory, aby bylo možné vyvolat Nástroj pro kompilátor nebo propojení z příkazového řádku, aniž by bylo nutné nastavit proměnnou prostředí **path** odpovídajícím způsobem.
