---
title: Závažná chyba C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: c425430a6d08ae8a97c4dcd0f5764f44dee43e5f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165863"
---
# <a name="fatal-error-c1902"></a>Závažná chyba C1902

Neshoda správce databáze programu; Zkontrolujte si prosím instalaci

Soubor databáze programu (PDB) byl vytvořen pomocí novější verze mspdb*XXX*.dll než ten, který kompilátor najít ve vašem systému. Tato chyba obvykle znamená, že mspdbsrv.exe mspdbcore.dll chybí nebo mají různé verze než mspdb*XXX*.dll. ( *XXX* zástupný symbol v mspdb*XXX*změny názvu souboru .dll s každou vydanou verzí produktu. Například v sadě Visual Studio 2015 název souboru je mspdb140.dll. Překontrolujte.)

Zkontrolujte odpovídající verzi mspdbsrv.exe mspdbcore.dll a mspdb*XXX*.dll jsou nainstalovány ve vašem systému. Ujistěte se, že verze nebyly zkopírovány do adresáře, který obsahuje nástroje kompilátor a odkaz pro cílovou platformu. Například zkopírovali jste soubory, je možné vyvolat z příkazového řádku bez nastavení nástroj kompilátor nebo odkaz **cesta** proměnnou prostředí odpovídajícím způsobem.