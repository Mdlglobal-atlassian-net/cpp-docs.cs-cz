---
title: Závažná chyba C1902 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1902
dev_langs:
- C++
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5a443b5f80eabe9691cf8ff5220bb9b66da51e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052559"
---
# <a name="fatal-error-c1902"></a>Závažná chyba C1902

Neshoda správce databáze programu; Zkontrolujte si prosím instalaci

Soubor databáze programu (PDB) byl vytvořen pomocí novější verze mspdb*XXX*.dll než ten, který kompilátor najít ve vašem systému. Tato chyba obvykle znamená, že mspdbsrv.exe mspdbcore.dll chybí nebo mají různé verze než mspdb*XXX*.dll. ( *XXX* zástupný symbol v mspdb*XXX*změny názvu souboru .dll s každou vydanou verzí produktu. Například v sadě Visual Studio 2015 název souboru je mspdb140.dll. Překontrolujte.)

Zkontrolujte odpovídající verzi mspdbsrv.exe mspdbcore.dll a mspdb*XXX*.dll jsou nainstalovány ve vašem systému. Ujistěte se, že verze nebyly zkopírovány do adresáře, který obsahuje nástroje kompilátor a odkaz pro cílovou platformu. Například zkopírovali jste soubory, je možné vyvolat z příkazového řádku bez nastavení nástroj kompilátor nebo odkaz **cesta** proměnnou prostředí odpovídajícím způsobem.