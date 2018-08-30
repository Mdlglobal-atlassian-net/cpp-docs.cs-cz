---
title: Csocketfile – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4c74d1ab89c45b7871cf0b4fa0d8a6350bc1425
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209634"
---
# <a name="csocketfile-class"></a>Csocketfile – třída
A `CFile` objektu se používá pro odesílání a přijímání dat přes síť prostřednictvím rozhraní Windows Sockets.  
  
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
 Můžete připojit `CSocketFile` do objektu `CSocket` objekt pro tento účel. Můžete také a obvykle, připojte `CSocketFile` do objektu `CArchive` objekt ke zjednodušení odesílání a přijímání dat pomocí knihovny MFC serializace.  
  
 K serializaci dat (Odeslat), můžete ho vložit do archivu, která volá `CSocketFile` členské funkce k zápisu dat `CSocket` objektu. K deserializaci (přijímání) data, rozbalte z archivu. To způsobí, že archivní úrovně do volání `CSocketFile` členské funkce pro čtení dat z `CSocket` objektu.  
  
> [!TIP]
>  Kromě použití `CSocketFile` podle postupu popsaného tady, můžete ho jako objekt do samostatného souboru, stejně jako u `CFile`, její základní třídy. Můžete také použít `CSocketFile` s žádné funkce na základě archivu serializace knihovny MFC. Protože `CSocketFile` nepodporuje všechny `CFile`je funkce, některé výchozí knihovny MFC serializovat funkce nejsou kompatibilní s `CSocketFile`. To platí hlavně `CEditView` třídy. By se neměl pokoušet serializovat `CEditView` data prostřednictvím `CArchive` objekt připojen k `CSocketFile` pomocí `CEditView::SerializeRaw`; použijte `CEditView::Serialize` místo. `SerializeRaw` Funkce očekává, že soubor objektu má funkce, jako například `Seek`, který `CSocketFile` nemá.  
  
 Při použití `CArchive` s `CSocketFile` a `CSocket`, může nastat situace, kdy `CSocket::Receive` přejde do smyčky (podle `PumpMessages(FD_READ)`) čekající na požadovaný počet bajtů. Důvodem je, že rozhraní Windows sockets povolit pouze jedno volání přijatých za FD_READ oznámení, ale `CSocketFile` a `CSocket` povolit více volání přijatých za FD_READ. Pokud dojde FD_READ když nejsou žádná data ke čtení, dojde k zablokování aplikace. Pokud obdržíte nikdy jiného FD_READ, že aplikace přestane komunikaci přes soket.  
  
 Tento problém lze vyřešit následovně. V `OnReceive` metoda třídy soketů, volání `CAsyncSocket::IOCtl(FIONREAD, ...)` před voláním `Serialize` metody třídy zpráv při očekávaná data ke čtení ze soketu překračuje velikost jednoho TCP paketu (MTU jednotky média sítě obvykle alespoň 1096 bajtů). Pokud velikost dostupných dat je menší než je potřeba, počkejte všechna data na přijmout a teprve potom začne operace čtení.  
  
 V následujícím příkladu `m_dwExpected` je přibližný počet bajtů, které uživatel očekává. Předpokládá se, že se deklaruje jinde ve vašem kódu.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]  
  
 Další informace najdete v tématu [Windows Sockets v prostředí MFC](../../mfc/windows-sockets-in-mfc.md), [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md), stejně jako [rozhraní Windows Sockets 2 API](/windows/desktop/WinSock/windows-sockets-start-page-2).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 `CSocketFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsock.h  
  
##  <a name="csocketfile"></a>  CSocketFile::CSocketFile  
 Vytvoří `CSocketFile` objektu.  
  
```  
explicit CSocketFile(
    CSocket* pSocket,  
    BOOL bArchiveCompatible = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pSocket*  
 Připojení k soketu `CSocketFile` objektu.  
  
 *bArchiveCompatible*  
 Určuje, zda je objekt souboru pro použití se službou `CArchive` objektu. Předejte hodnotu FALSE, pouze v případě, že chcete použít `CSocketFile` objektu v podobě samostatné, stejně jako samostatná `CFile` objektu s některými omezeními. Tento příznak změní způsob, jakým `CArchive` objekt připojen k `CSocketFile` objekt spravuje vyrovnávací paměti pro čtení.  
  
### <a name="remarks"></a>Poznámky  
 Destruktor objektu zruší přidružení samotné z objekt soketu při dostane mimo rozsah nebo odstranění objektu.  
  
> [!NOTE]
>  A `CSocketFile` slouží také jako soubor (omezený) bez `CArchive` objektu. Ve výchozím nastavení `CSocketFile` konstruktoru *bArchiveCompatible* parametr má hodnotu TRUE. Určuje, že objekt souboru je pro použití s archivu. Pokud chcete použít soubor objektu bez archiv, předejte hodnotu FALSE, v *bArchiveCompatible* parametru.  
  
 V režimu "archivu compatible" `CSocketFile` objekt poskytuje lepší výkon a snižuje nebezpečí "zablokování." K zablokování dochází tehdy, když čekají na přiřazení a odesílající sokety na sobě navzájem, nebo pro běžné zdroje. Tato situace může nastat, pokud `CArchive` objektu ve spolupráci s `CSocketFile` tak, jak to funguje se službou `CFile` objektu. S `CFile`, archivu můžete předpokládat, že pokud obdrží méně bajtů než je požadováno, na konci souboru se dosáhlo.  
  
 S `CSocketFile`, ale data jsou zprávy na základě; vyrovnávací paměti může obsahovat více zpráv, tak přijímá méně než počet bajtů neznamená konec souboru. Aplikace není v tomto případě blokování, jak se může stát, že se `CFile`, a můžete pokračovat, přečte zprávy z vyrovnávací paměti, dokud vyrovnávací paměť je prázdná. [CArchive::IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) funkce je užitečná pro sledování stavu archivu vyrovnávací paměti v takovém případě.  
  
 Další informace týkající se použití `CSocketFile`, najdete v článcích [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md) a [rozhraní Windows Sockets: příklad z Sockets pomocí archivy](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="see-also"></a>Viz také  
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Casyncsocket – třída](../../mfc/reference/casyncsocket-class.md)   
 [CSocket – třída](../../mfc/reference/csocket-class.md)
