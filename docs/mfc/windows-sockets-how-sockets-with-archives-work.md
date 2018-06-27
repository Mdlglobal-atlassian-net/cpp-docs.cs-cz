---
title: 'Windows Sockets: Jak pracují sokety s archivy | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c4f581acb0af27f44c88d59597e52b057991ee4
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954276"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets: Jak pracují sokety s archivy
Tento článek vysvětluje, jak [CSocket](../mfc/reference/csocket-class.md) objekt, [CSocketFile](../mfc/reference/csocketfile-class.md) objekt a [CArchive](../mfc/reference/carchive-class.md) objekt se zkombinují zjednodušit odesílat a přijímat data prostřednictvím systému Windows Časový limit soketu.  
  
 Článek [Windows Sockets: příklad z Sockets pomocí archivy](../mfc/windows-sockets-example-of-sockets-using-archives.md) uvede `PacketSerialize` funkce. Objekt archivu v `PacketSerialize` příklad funguje podobně jako archiv objekt předaný knihovny MFC [serializace](../mfc/reference/cobject-class.md#serialize) funkce. Základní rozdíl je, zda sokety, archivu připojený není pro standardní [cfile –](../mfc/reference/cfile-class.md) objekt (obvykle přidružený soubor na disku) ale položky `CSocketFile` objektu. Místo připojení do souboru na disku `CSocketFile` objekt připojí k `CSocket` objektu.  
  
 A `CArchive` objekt spravuje vyrovnávací paměti. Při ukládání (odesílajícím) archivu vyrovnávací paměť je plná, přiřazený `CFile` objekt zapíše se do vyrovnávací paměti obsah. Probíhá vyprazdňování vyrovnávací paměti archivu připojit k soketu je ekvivalentní volání odesílání zprávy. Po zaplnění vyrovnávací paměti načtení (příjem) archivu `CFile` objekt čtení přestane, dokud vyrovnávací paměť je opět k dispozici.  
  
 Třída `CSocketFile` je odvozena z `CFile`, ale nepodporuje [cfile –](../mfc/reference/cfile-class.md) členské funkce jako je například umísťovací funkce (`Seek`, `GetLength`, `SetLength`a tak dále), blokovací funkce ( `LockRange`, `UnlockRange`), nebo `GetPosition` funkce. Všechny [CSocketFile](../mfc/reference/csocketfile-class.md) musíte udělat objektu je zápisu nebo čtení pořadí bajtů do nebo z přidruženého `CSocket` objektu. Vzhledem k tomu, že soubor není zahrnut, operace, jako `Seek` a `GetPosition` žádné smysl. `CSocketFile` je odvozený od `CFile`, takže by za normálních okolností zdědit všechny tyto členských funkcí. Chcete-li tomu zabránit, nepodporovanou `CFile` členské funkce jsou přepsaná v `CSocketFile` má být vyvolána [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md).  
  
 `CSocketFile` Objekt volání členských funkcí jeho `CSocket` objekt, který chcete odesílat nebo přijímat data.  
  
 Následující obrázek znázorňuje vztahy mezi tyto objekty na obou stranách komunikace.  
  
 ![CArchive, CSocketFile a CSocket](../mfc/media/vc38ia1.gif "vc38ia1")  
CArchive, CSocketFile a CSocket  
  
 Účelem této zřejmá složitost je vás chrání před nezbytné podrobnosti o soketu správy sami. Můžete vytvořit soket, souboru a archivu a pak začněte odesílání nebo příjmu dat tím, že vkládání do archivu nebo extrahování z archivu. [CArchive](../mfc/reference/carchive-class.md), [CSocketFile](../mfc/reference/csocketfile-class.md), a [CSocket](../mfc/reference/csocket-class.md) Správa podrobností na pozadí.  
  
 A `CSocket` objekt je ve skutečnosti objekt dvou stavů: v některých případech asynchronní (obvykle stav) a někdy synchronní. V jeho asynchronní stavu může přijímat soket asynchronní oznámení z rozhraní. Během operace jako příjem nebo odeslání dat stane však synchronní soketu. To znamená, že soketem obdrží žádné další asynchronní oznámení, dokud se nedokončí synchronní operace. Protože Přepíná režimy, můžete, například provést přibližně takto:  
  
 [!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]  
  
 Pokud `CSocket` nebyla implementována jako objekt dvou stavů, je možné přijímat další oznámení pro stejný druh události při byly zpracování předchozí oznámení. Například může získat `OnReceive` během zpracování oznámení `OnReceive`. Ve výše uvedené fragmentu kódu extrahování `str` z archivu může vést k rekurzi. Přepnutím stavy, `CSocket` brání rekurze tím, že další oznámení. Obecným pravidlem je žádná oznámení v rámci oznámení.  
  
> [!NOTE]
>  A `CSocketFile` lze také použít jako soubor (omezený) bez `CArchive` objektu. Ve výchozím nastavení `CSocketFile` konstruktoru *bArchiveCompatible* parametr **TRUE**. To určuje, že objekt souboru je pro použití s archivu. Chcete-li použít objekt souboru bez archiv, předat **FALSE** v *bArchiveCompatible* parametr.  
  
 V režimu "archivu compatible" `CSocketFile` objekt poskytuje lepší výkon a snižuje nebezpečí "vzájemné zablokování." Dojde k zablokování, když přijímající a odesílající sokety jsou čekání na sobě navzájem nebo čeká na běžné prostředek. Tato situace může nastat, pokud `CArchive` objekt pracoval s `CSocketFile` způsob, jak v případě `CFile` objektu. S `CFile`, archivu můžete předpokládat, že pokud obdrží menší počet bajtů, než je požadováno, na konci souboru byl dosažen. S `CSocketFile`, ale data jsou zprávy založené; vyrovnávací paměti může obsahovat více zpráv, tak přijímá menší než počet bajtů neznamená konec souboru. Aplikace v tomto případě neblokuje což se může stát s `CFile`, a můžete pokračovat, dokud vyrovnávací paměť je prázdná čtení zpráv z vyrovnávací paměti. [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty) fungovat v `CArchive` je užitečná pro sledování stavu do archivu vyrovnávací paměti v tomto případě.  
  
 Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## <a name="see-also"></a>Viz také  
 [Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)   
 [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)

