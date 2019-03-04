---
title: Zavírání souborů
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: 69a0960c1edabab00cb71702acda526ee9ebd798
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267053"
---
# <a name="closing-files"></a>Zavírání souborů

Jako obvykle ve vstupně-výstupních operací, po dokončení se souborem, je zapotřebí jej zavřít.

#### <a name="to-close-a-file"></a>Zavřete soubor

1. Použití **Zavřít** členskou funkci. Tato funkce zavře soubor, který systém souborů a v případě potřeby vyprázdní vyrovnávací paměti.

Pokud jste přidělili [cfile –](../mfc/reference/cfile-class.md) objekt v rámci (stejně jako v příkladu v [otevírání souborů](../mfc/opening-files.md)), objekt bude automaticky zavřít a následně zničeny, když dostane mimo rozsah. Všimněte si, že odstranění `CFile` objekt nedojde k odstranění fyzického souboru v systému souborů.

## <a name="see-also"></a>Viz také:

[Soubory](../mfc/files-in-mfc.md)
