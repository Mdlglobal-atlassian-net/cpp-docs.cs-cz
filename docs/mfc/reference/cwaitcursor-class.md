---
title: Cwaitcursor – třída
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 7ce81e62ec6498ad84349108b4c4a07090b17de5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287128"
---
# <a name="cwaitcursor-class"></a>Cwaitcursor – třída

Poskytuje jednořádkový způsob, jak zobrazit kurzor pro čekání, obvykle zobrazený jako přesýpací hodiny, zatímco provádíte dlouhotrvající operace.

## <a name="syntax"></a>Syntaxe

```
class CWaitCursor
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Vytvoří `CWaitCursor` objektu a zobrazí kurzor pro čekání.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWaitCursor::Restore](#restore)|Obnoví kurzor pro čekání po byl změněn.|

## <a name="remarks"></a>Poznámky

`CWaitCursor` nemá základní třídu.

Programovací postupy vhodné Windows vyžadují zobrazit kurzor pro čekání pokaždé, když se při provádění operace, která trvá určitou dobu.

Chcete-li zobrazit kurzor pro čekání, stačí definovat `CWaitCursor` proměnné před kód, který provádí časově náročná operace. Konstruktor objektu automaticky způsobí, že se kurzor pro čekání má být zobrazen.

Pokud objekt dostane mimo rozsah (na konci bloku, ve kterém `CWaitCursor` deklaraci objektu), jeho destruktor nastaví kurzor na předchozí kurzor. Jinými slovy objekt provádí automaticky potřebné vyčištění.

> [!NOTE]
>  Z důvodu jejich konstruktory a destruktory fungování `CWaitCursor` objekty jsou vždy deklarované jako lokální proměnné – nikdy jsou deklarovány jako globální proměnné ani se přidělují s **nové**.

Pokud provádíte operaci, což by mohlo způsobit kurzor, který se změnil, jako je například zobrazení okna se zprávou nebo dialogové okno, volání [obnovení](#restore) členskou funkci obnovení kurzor pro čekání. Je možné volat `Restore` i když kurzor pro čekání se nyní zobrazí.

Dalším způsobem, jak zobrazit kurzor pro čekání je určený kombinací [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)a případně [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Nicméně `CWaitCursor` je jednodušší použít, protože není nutné nastavte kurzor na předchozí kurzor, až budete hotovi s časově náročná operace.

> [!NOTE]
>  Nastaví knihovny MFC a obnoví pomocí kurzoru [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) virtuální funkce. Tato funkce se vlastní chování můžete přepsat.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CWaitCursor`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

##  <a name="cwaitcursor"></a>  CWaitCursor::CWaitCursor

Chcete-li zobrazit kurzor pro čekání, stačí deklarovat `CWaitCursor` objektu před kód, který provádí časově náročná operace.

```
CWaitCursor();
```

### <a name="remarks"></a>Poznámky

Konstruktor automaticky způsobí, že se kurzor pro čekání má být zobrazen.

Pokud objekt dostane mimo rozsah (na konci bloku, ve kterém `CWaitCursor` deklaraci objektu), jeho destruktor nastaví kurzor na předchozí kurzor. Jinými slovy objekt provádí automaticky potřebné vyčištění.

Můžete využít výhod skutečnost, že je zavolán destruktor na konci bloku (který může být před ukončením funkce) aby kurzor pro čekání aktivní jenom část vaší funkce. Tato technika je zobrazena ve druhém níže uvedeném příkladu.

> [!NOTE]
>  Z důvodu jejich konstruktory a destruktory fungování `CWaitCursor` objekty jsou vždy deklarované jako lokální proměnné – nikdy jsou deklarovány jako globální proměnné ani se přidělují s **nové**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

##  <a name="restore"></a>  CWaitCursor::Restore

Chcete-li obnovit kurzor pro čekání, voláním této funkce po provedení operace, jako je například zobrazení okna se zprávou nebo dialogové okno, které mohou změnit kurzor pro čekání na jiný kurzor.

```
void Restore();
```

### <a name="remarks"></a>Poznámky

Je možné volat `Restore` i když kurzor pro čekání se nyní zobrazí.

Pokud potřebujete obnovit kurzor pro čekání ve funkci než ten, ve kterém `CWaitCursor` deklaraci objektu, můžete volat [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Postup: Změnit kurzoru myši v aplikaci tříd Microsoft Foundation](http://go.microsoft.com/fwlink/p/?linkid=128044)
