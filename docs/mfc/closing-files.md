---
title: Zavírání souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c392ef728e1d796a02cfa32edc2c3e8c74d083b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426234"
---
# <a name="closing-files"></a>Zavírání souborů

Jako obvykle ve vstupně-výstupních operací, po dokončení se souborem, je zapotřebí jej zavřít.

#### <a name="to-close-a-file"></a>Zavřete soubor

1. Použití **Zavřít** členskou funkci. Tato funkce zavře soubor, který systém souborů a v případě potřeby vyprázdní vyrovnávací paměti.

Pokud jste přidělili [cfile –](../mfc/reference/cfile-class.md) objekt v rámci (stejně jako v příkladu v [otevírání souborů](../mfc/opening-files.md)), objekt bude automaticky zavřít a následně zničeny, když dostane mimo rozsah. Všimněte si, že odstranění `CFile` objekt nedojde k odstranění fyzického souboru v systému souborů.

## <a name="see-also"></a>Viz také

[Soubory](../mfc/files-in-mfc.md)

