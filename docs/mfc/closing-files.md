---
title: Zavírání souborů
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 04e5084615b1f1cf85d9f41e2c4dcc84910b9d05
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636260"
---
# <a name="closing-files"></a>Zavírání souborů

Jako obvykle ve vstupně-výstupních operací, po dokončení se souborem, je zapotřebí jej zavřít.

#### <a name="to-close-a-file"></a>Zavřete soubor

1. Použití **Zavřít** členskou funkci. Tato funkce zavře soubor, který systém souborů a v případě potřeby vyprázdní vyrovnávací paměti.

Pokud jste přidělili [cfile –](../mfc/reference/cfile-class.md) objekt v rámci (stejně jako v příkladu v [otevírání souborů](../mfc/opening-files.md)), objekt bude automaticky zavřít a následně zničeny, když dostane mimo rozsah. Všimněte si, že odstranění `CFile` objekt nedojde k odstranění fyzického souboru v systému souborů.

## <a name="see-also"></a>Viz také

[Soubory](../mfc/files-in-mfc.md)

