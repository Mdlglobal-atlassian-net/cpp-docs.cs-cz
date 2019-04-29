---
title: Jak prostředí MFC usnadňuje tvorbu internetových klientských aplikací
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: ffeed3a844fb86acf1bf8c5181c59529824c27f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405752"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Jak prostředí MFC usnadňuje tvorbu internetových klientských aplikací

Microsoft Foundation Classes zapouzdřují funkce Win32 internetová rozšíření (WinInet) způsobem, který poskytuje Známé kontext usnadňuje práci programátorům knihovny MFC. Knihovna MFC poskytuje tři třídy souborů Internetu ([cinternetfile –](../mfc/reference/cinternetfile-class.md), [chttpfile –](../mfc/reference/chttpfile-class.md), a [cgopherfile –](../mfc/reference/cgopherfile-class.md)) odvozený od [cstdiofile –](../mfc/reference/cstdiofile-class.md) třídy . Nejen těchto tříd Ujistěte se, načítání a manipulace s daty Internet pro programátory, kteří použili srozumitelná `CStdioFile` místních souborů, ale s tyto třídy můžete zpracovávat místní soubory a soubory Internetu konzistentní vzhledem k aplikacím a transparentní způsobem.

Tříd WinInet knihovny MFC poskytují stejné funkce jako `CStdioFile` pro data, která se přenáší přes Internet. Tyto třídy abstraktní Internetové protokoly HTTP, FTP a gopher na vysoké úrovni aplikaci programování rozhraní, poskytuje rychlý a jednoduchý cestu k vytváření aplikací s ohledem na Internetu. Například připojení k serveru FTP stále vyžaduje několik kroků na nízké úrovni, ale jako vývojář knihovny MFC, je potřeba jenom jeden hovor `CInternetSession::GetFTPConnection` vytvořit toto připojení.

Kromě toho tříd WinInet knihovny MFC poskytují následující výhody:

- Vstupně-výstupních operací ve vyrovnávací paměti

- Typově bezpečný zpracovává vaše data

- Výchozí parametry pro mnoho funkcí

- Zpracování výjimek pro běžné chyby Internet

- Automatické čištění připojení a otevřených popisovačů

## <a name="see-also"></a>Viz také:

[Win32 – internetová rozšíření (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Jak rozhraní WinInet usnadňuje tvorbu internetových klientských aplikací](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)
