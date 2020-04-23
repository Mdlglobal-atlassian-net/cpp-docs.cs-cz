---
title: Třída CWaitCursor
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
ms.openlocfilehash: aaa60e26d0a9bf99076f29124097b0629ce6f5d0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754328"
---
# <a name="cwaitcursor-class"></a>Třída CWaitCursor

Poskytuje jednořádkový způsob zobrazení kurzoru čekání, který se obvykle zobrazuje jako přesýpací hodiny, zatímco provádíte zdlouhavou operaci.

## <a name="syntax"></a>Syntaxe

```
class CWaitCursor
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Vytvoří `CWaitCursor` objekt a zobrazí kurzor čekání.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CWaitCursor::Obnovit](#restore)|Obnoví kurzor čekání po jeho změně.|

## <a name="remarks"></a>Poznámky

`CWaitCursor`nemá základní třídu.

Dobré postupy programování systému Windows vyžadují, abyste při každé operaci, která trvá znatelně, zobrazili kurzor čekání.

Chcete-li zobrazit kurzor `CWaitCursor` čekání, stačí definovat proměnnou před kódem, který provádí zdlouhavou operaci. Konstruktor objektu automaticky způsobí, že kurzor čekání se zobrazí.

Když objekt přejde mimo rozsah (na konci bloku, ve kterém je `CWaitCursor` deklarován objekt), jeho destruktor nastaví kurzor na předchozí kurzor. Jinými slovy objekt provede potřebné vyčištění automaticky.

> [!NOTE]
> Vzhledem k tomu, jak jejich konstruktory `CWaitCursor` a destruktory práce, objekty jsou vždy deklarovány jako místní proměnné – jsou nikdy deklarovány jako globální proměnné, ani jsou přiděleny s **novým**.

Pokud provedete operaci, která může způsobit změnu kurzoru, například zobrazení okna se zprávou nebo dialogového okna, zavolejte [obnovení](#restore) členské funkce a obnovte kurzor čekání. Je v pořádku `Restore` volat i v případě, že je aktuálně zobrazen kurzor čekání.

Dalším způsobem, jak zobrazit kurzor čekání je použít kombinaci [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)a možná [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Je `CWaitCursor` však jednodušší, protože není nutné nastavit kurzor na předchozí kurzor, když jste hotovi s dlouhou operaci.

> [!NOTE]
> Knihovna MFC nastaví a obnoví kurzor pomocí virtuální funkce [CWinApp::DoWaitCursor.](../../mfc/reference/cwinapp-class.md#dowaitcursor) Tuto funkci můžete přepsat a poskytnout tak vlastní chování.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CWaitCursor`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor::CWaitCursor

Chcete-li zobrazit kurzor `CWaitCursor` čekání, stačí deklarovat objekt před kódem, který provádí zdlouhavou operaci.

```
CWaitCursor();
```

### <a name="remarks"></a>Poznámky

Konstruktor automaticky způsobí, že kurzor čekání se zobrazí.

Když objekt přejde mimo rozsah (na konci bloku, ve kterém je `CWaitCursor` deklarován objekt), jeho destruktor nastaví kurzor na předchozí kurzor. Jinými slovy objekt provede potřebné vyčištění automaticky.

Můžete využít skutečnost, že destruktor je volána na konci bloku (což může být před koncem funkce) chcete-li, aby kurzor čekání aktivní pouze v části funkce. Tato technika je uvedena v druhém příkladu níže.

> [!NOTE]
> Vzhledem k tomu, jak jejich konstruktory `CWaitCursor` a destruktory práce, objekty jsou vždy deklarovány jako místní proměnné – jsou nikdy deklarovány jako globální proměnné, ani jsou přiděleny s **novým**.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor::Obnovit

Chcete-li obnovit kurzor čekání, zavolejte tuto funkci po provedení operace, jako je například zobrazení okna se zprávou nebo dialogového okna, které může změnit kurzor čekání na jiný kurzor.

```cpp
void Restore();
```

### <a name="remarks"></a>Poznámky

Je v pořádku `Restore` volat i v případě, že je aktuálně zobrazen kurzor čekání.

Pokud potřebujete obnovit kurzor čekání v jiné funkci než `CWaitCursor` ve které je objekt deklarován, můžete volat [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Jak se mi: Změna kurzoru myši v aplikaci třídy Microsoft Foundation](https://go.microsoft.com/fwlink/p/?linkid=128044)
