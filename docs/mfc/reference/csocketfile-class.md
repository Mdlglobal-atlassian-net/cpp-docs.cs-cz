---
title: "Třída CSocketFile | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
dev_langs:
- C++
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 48ab1428d2c02e51b02977c8457d28e20597cbb7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csocketfile-class"></a>CSocketFile – třída
A `CFile` objekt používaný pro odesílání a příjmu dat přes síť pomocí rozhraní Windows Sockets.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSocketFile : public CFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSocketFile::CSocketFile](#csocketfile)|Vytvoří `CSocketFile` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete připojit `CSocketFile` do objektu `CSocket` objekt pro tento účel. Také můžete a obvykle, připojte `CSocketFile` do objektu `CArchive` objekt zjednodušení odesílat a přijímat data pomocí MFC serializace.  
  
 K serializaci dat (Odeslat), můžete ji vložit do archivu, který volá `CSocketFile` členské funkce zapsat data do `CSocket` objektu. K deserializaci (přijímat) data, rozbalte z archivu. To způsobí, že archivu volat `CSocketFile` členské funkce Číst data z `CSocket` objektu.  
  
> [!TIP]
>  Kromě použití `CSocketFile` podle postupu popsaného tady, můžete ho jako objekt samostatného souboru, stejně jako v `CFile`, jeho základní třída. Můžete také použít `CSocketFile` s všechny funkce na základě archivu serializace MFC. Protože `CSocketFile` nepodporuje všechny `CFile`je funkce, některé výchozí MFC serializovat funkce nejsou kompatibilní s `CSocketFile`. To platí hlavně z `CEditView` třídy. By se neměl pokoušet serializovat `CEditView` data prostřednictvím `CArchive` objekt připojený k `CSocketFile` pomocí `CEditView::SerializeRaw`; použít **CEditView::Serialize** místo. `SerializeRaw` Funkce očekává objektu soubor do mají funkce, jako například `Seek`, že `CSocketFile` nemá.  
  
 Při použití `CArchive` s `CSocketFile` a `CSocket`, může nastat situace, kdy **CSocket::Receive** zadá smyčku (podle **PumpMessages(FD_READ)**) čekání požadovaný počet bajtů. Důvodem je, že rozhraní Windows sockets povolit pouze jedno volání přijatých za FD_READ oznámení, ale `CSocketFile` a `CSocket` povolit více volání přijatých za FD_READ. Pokud dojde FD_READ po žádná data ke čtení, dojde k zablokování aplikace. Pokud se nikdy jiné FD_READ, aplikace přestane komunikaci přes soketu.  
  
 Tento problém můžete vyřešit následujícím způsobem. V `OnReceive` metoda třídy soketů, volání **CAsyncSocket::IOCtl (FIONREAD,...)**  před voláním `Serialize` metoda třídě zpráv při čtení ze soketu očekávaná data překračuje velikost jednoho paketu protokolu TCP (hodnota MTU střední sítě, obvykle alespoň 1096 bajtů). Pokud velikost dostupné dat je menší než je potřeba, počkejte všechna data a přijímat pouze spusťte operace čtení.  
  
 V následujícím příkladu `m_dwExpected` je přibližný počet bajtů, které uživatel očekává. Předpokládá se, že deklarujete ho jinde v kódu.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]  
  
 Další informace najdete v tématu [Windows Sockets v prostředí MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md), a také [rozhraní API systému Windows Sockets 2](http://msdn.microsoft.com/library/windows/desktop/ms740673).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsock.h  
  
##  <a name="csocketfile"></a>CSocketFile::CSocketFile  
 Vytvoří `CSocketFile` objektu.  
  
```  
explicit CSocketFile(
    CSocket* pSocket,  
    BOOL bArchiveCompatible = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `pSocket`  
 Připojit k soketu `CSocketFile` objektu.  
  
 `bArchiveCompatible`  
 Určuje, zda je objekt souboru pro použití s `CArchive` objektu. Předat **FALSE** pouze v případě, že chcete použít `CSocketFile` objektu samostatné způsobem jako samostatný `CFile` objekt s některými omezeními. Tento příznak změny jak `CArchive` objekt připojený k `CSocketFile` objekt spravuje vyrovnávací paměti pro čtení.  
  
### <a name="remarks"></a>Poznámky  
 Destruktoru objektu zrušíte sám sebe z objektu soketu při objekt ocitne mimo rozsah, nebo je odstranit.  
  
> [!NOTE]
>  A `CSocketFile` lze také použít jako soubor (omezený) bez `CArchive` objektu. Ve výchozím nastavení `CSocketFile` konstruktoru `bArchiveCompatible` parametr **TRUE**. To určuje, že objekt souboru je pro použití s archivu. Chcete-li použít objekt souboru bez archiv, předat **FALSE** v `bArchiveCompatible` parametr.  
  
 V režimu "archivu compatible" `CSocketFile` objekt poskytuje lepší výkon a snižuje nebezpečí "vzájemné zablokování." Dojde k zablokování, když přijímající a odesílající sokety čekají na sobě navzájem, nebo pro běžné prostředků. Tato situace může nastat, pokud `CArchive` objekt pracoval s `CSocketFile` způsob, jak v případě `CFile` objektu. S `CFile`, archivu můžete předpokládat, že pokud obdrží menší počet bajtů, než je požadováno, na konci souboru byl dosažen.  
  
 S `CSocketFile`, ale data jsou zprávy založené; vyrovnávací paměti může obsahovat více zpráv, tak přijímá menší než počet bajtů neznamená konec souboru. Aplikace v tomto případě neblokuje což se může stát s `CFile`, a můžete pokračovat, dokud vyrovnávací paměť je prázdná čtení zpráv z vyrovnávací paměti. [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) funkce je užitečná pro sledování stavu do archivu vyrovnávací paměti v tomto případě.  
  
 Další informace o použití `CSocketFile`, najdete v článcích [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md) a [Windows Sockets: příklad z Sockets pomocí archivy](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="see-also"></a>Viz také  
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket – třída](../../mfc/reference/casyncsocket-class.md)   
 [CSocket – třída](../../mfc/reference/csocket-class.md)
