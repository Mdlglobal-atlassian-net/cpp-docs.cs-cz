---
title: Třídy I/o souborů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.file
dev_langs:
- C++
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad854b054ca32819597126c5a4c0b9652df9210
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442133"
---
# <a name="file-io-classes"></a>Třídy I/O souborů

Tyto třídy poskytuje rozhraní pro tradiční disku souborů v paměti, aktivní datové proudy a rozhraní Windows sockets. Všechny třídy odvozené z `CFile` jde použít s `CArchive` objekt pro provedení serializace.

Použijte následující třídy, zejména `CArchive` a `CFile`, můžete psát vlastní zpracování vstupu a výstupu. Není obvykle nutné odvozovat z těchto tříd. Pokud používáte rozhraní framework aplikace výchozí implementace **otevřít** a **Uložit** příkazy na **souboru** nabídky bude zpracovávat vstup a výstup souborů (horizontálních oddílů pomocí třídy `CArchive`), tak dlouho, dokud je přepsat váš dokument `Serialize` funkce k zadání podrobností o jak dokumentu serializuje jeho obsah. Další informace o souboru třídy a serializaci, najdete v článku [soubory v prostředí MFC](../mfc/files-in-mfc.md) a článek [serializace](../mfc/serialization-in-mfc.md).

[Cfile –](../mfc/reference/cfile-class.md)<br/>
Poskytuje rozhraní souborů na disku binární soubory.

[Cstdiofile –](../mfc/reference/cstdiofile-class.md)<br/>
Poskytuje `CFile` rozhraní do souborů disku uložené do vyrovnávací paměti datového proudu, obvykle v textovém režimu.

[Cmemfile –](../mfc/reference/cmemfile-class.md)<br/>
Poskytuje `CFile` rozhraní do souborů v paměti.

[Csharedfile –](../mfc/reference/csharedfile-class.md)<br/>
Poskytuje `CFile` rozhraní sdílené soubory v paměti.

[Colestreamfile –](../mfc/reference/colestreamfile-class.md)<br/>
Používá COM `IStream` rozhraní k poskytování `CFile` přístup k složené soubory.

[Csocketfile –](../mfc/reference/csocketfile-class.md)<br/>
Poskytuje `CFile` rozhraní Windows Socket.

## <a name="related-classes"></a>Související třídy

[CArchive](../mfc/reference/carchive-class.md)<br/>
Spolupracuje s `CFile` objektu pro implementaci trvalého úložiště pro objekty prostřednictvím serializace (viz [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).

[Carchiveexception –](../mfc/reference/carchiveexception-class.md)<br/>
Výjimku archivu.

[Cfileexception –](../mfc/reference/cfileexception-class.md)<br/>
Soubor objektově orientovaný výjimky.

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
Poskytuje standardní dialogové okno pro otevření nebo uložení souboru.

[Crecentfilelist –](../mfc/reference/crecentfilelist-class.md)<br/>
Uchovává poslední použitou seznam souborů (MRU).

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

