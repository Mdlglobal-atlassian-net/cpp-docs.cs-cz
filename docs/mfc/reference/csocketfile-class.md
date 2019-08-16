---
title: CSocketFile – třída
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: 3b969f81c0c6e1868a66aeaa1c4d9339792062df
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502451"
---
# <a name="csocketfile-class"></a>CSocketFile – třída

`CFile` Objekt používaný k posílání a přijímání dat napříč sítí přes Windows Sockets.

## <a name="syntax"></a>Syntaxe

```
class CSocketFile : public CFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSocketFile::CSocketFile](#csocketfile)|`CSocketFile` Vytvoří objekt.|

## <a name="remarks"></a>Poznámky

`CSocketFile` Objekt lze pro tento účel připojit `CSocket` k objektu. Můžete také a obvykle připojit `CSocketFile` objekt `CArchive` k objektu pro zjednodušení odesílání a příjem dat pomocí serializace knihovny MFC.

Chcete-li serializovat data (odeslání), vložte je do archivu, který volá `CSocketFile` členské funkce pro zápis dat `CSocket` do objektu. K deserializaci (příjmu) dat extrahujete z archivu. To způsobí, že archiv bude `CSocketFile` volat členské funkce pro čtení dat `CSocket` z objektu.

> [!TIP]
>  Kromě použití `CSocketFile` , jak je popsáno zde, můžete použít jako objekt samostatného souboru, stejně jako s `CFile`, jeho základní třídou. Můžete také použít `CSocketFile` s jakoukoli archivní funkcí serializace knihovny MFC. Vzhledem `CSocketFile` k tomu, že nepodporuje `CFile`všechny funkce, nejsou některé výchozí funkce serializace knihovny MFC kompatibilní `CSocketFile`s. To platí zejména pro `CEditView` třídu. Neměli byste se pokoušet o serializaci `CEditView` dat `CArchive` prostřednictvím objektu připojeného k `CSocketFile` objektu pomocí `CEditView::SerializeRaw`; použijte `CEditView::Serialize` místo toho. Funkce očekává, že objekt File má funkce, `Seek`jako například, který `CSocketFile` nemá. `SerializeRaw`

`CArchive` Pokud používáte s `CSocketFile` a `CSocket`, může dojít `CSocket::Receive` ksituaci,kdyvstoupí`PumpMessages(FD_READ)`do smyčky čekání na požadovaný počet bajtů. Důvodem je to, že sokety systému Windows umožňují pouze jedno přijmout volání na `CSocketFile` oznámení `CSocket` FD_READ, ale a umožňují více přijmout volání na FD_READ. Pokud se zobrazí FD_READ, když nejsou k dispozici žádná data ke čtení, aplikace přestane reagovat. Pokud nikdy nezískáte další FD_READ, aplikace přestane komunikovat přes soket.

Tento problém můžete vyřešit následujícím způsobem. V metodě třídy soketu volejte `CAsyncSocket::IOCtl(FIONREAD, ...)` před voláním `Serialize` metody vaší třídy zpráv, když očekávaná data, která mají být načtena ze soketu, překročí velikost jednoho paketu TCP (maximální přenosová jednotka síťového média `OnReceive` , obvykle alespoň 1096 bajtů). Pokud je velikost dostupných dat menší, než je potřeba, počkejte na přijetí všech dat a pak spusťte operaci čtení.

V následujícím příkladu `m_dwExpected` je přibližný počet bajtů, které uživatel očekává k přijetí. Předpokládá se, že deklarujete ho jinde ve svém kódu.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

Další informace najdete v tématu rozhraní [Windows Sockets v knihovně MFC](../../mfc/windows-sockets-in-mfc.md), [rozhraní Windows Sockets: Použití soketů s](../../mfc/windows-sockets-using-sockets-with-archives.md)archivy i [rozhraní Windows Sockets 2 API](/windows/win32/WinSock/windows-sockets-start-page-2).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AfxSock. h

##  <a name="csocketfile"></a>CSocketFile::CSocketFile

`CSocketFile` Vytvoří objekt.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>Parametry

*pSocket*<br/>
Soket, který se má připojit `CSocketFile` k objektu.

*bArchiveCompatible*<br/>
Určuje, zda je objekt souboru určen pro použití s `CArchive` objektem. Předejte hodnotu false pouze v případě, že `CSocketFile` chcete objekt použít pouze v samostatném způsobem, který by měl být `CFile` samostatným objektem s určitými omezeními. Tento příznak mění způsob, `CArchive` jakým objekt připojený `CSocketFile` k objektu spravuje svou vyrovnávací paměť pro čtení.

### <a name="remarks"></a>Poznámky

Destruktor objektu zruší přidružení sebe sama od objektu soketu, když se objekt dostane mimo rozsah nebo je odstraněn.

> [!NOTE]
>  Lze také použít jako (omezený) soubor `CArchive` bez objektu. `CSocketFile` Ve výchozím nastavení `CSocketFile` má parametr *bArchiveCompatible* konstruktoru hodnotu true. Tím se určuje, že objekt souboru je určen pro použití s archivem. Chcete-li použít objekt File bez archivu, předejte hodnotu FALSE do parametru *bArchiveCompatible* .

V režimu `CSocketFile` "kompatibilní s archivem" objekt poskytuje lepší výkon a snižuje nebezpečí zablokování. K zablokování dojde, když odesílající i přijímací sokety čekají na sebe nebo pro společný prostředek. K této situaci může dojít, `CArchive` je-li objekt `CSocketFile` pracoval se `CFile` způsobem, který s objektem pracuje. `CFile`V případě může archiv předpokládat, že pokud obdrží méně bajtů, než bylo vyžádáno, bylo dosaženo konce souboru.

`CSocketFile`Data jsou však založena na zprávách. vyrovnávací paměť může obsahovat více zpráv, takže když přijímají méně než počet požadovaných bajtů, neznamená to konec souboru. Aplikace v tomto případě neblokuje v tomto případě `CFile`a může pokračovat v čtení zpráv z vyrovnávací paměti, dokud není vyrovnávací paměť prázdná. Funkce [CArchive:: IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) je užitečná pro monitorování stavu vyrovnávací paměti archivu v takovém případě.

Další informace o použití `CSocketFile`nástroje najdete v článcích [Windows Sockets: Použití soketů s](../../mfc/windows-sockets-using-sockets-with-archives.md) archivy a [Windows Sockets: Příklad soketů využívajících](../../mfc/windows-sockets-example-of-sockets-using-archives.md)archivy.

## <a name="see-also"></a>Viz také:

[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket – třída](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket – třída](../../mfc/reference/csocket-class.md)
