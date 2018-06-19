---
title: Třída CWaitCursor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs:
- C++
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e7bc4755d2e96c78735f1b3ef175ff3603686fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372505"
---
# <a name="cwaitcursor-class"></a>CWaitCursor – třída
Poskytuje způsob jednořádkové čekání kurzor, který je obvykle zobrazený jako přesýpací hodiny, když provádíte časově náročná operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWaitCursor  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Vytvoří `CWaitCursor` objektu a zobrazí kurzor čekání.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CWaitCursor::Restore](#restore)|Obnoví kurzor čekání po byl změněn.|  
  
## <a name="remarks"></a>Poznámky  
 `CWaitCursor` nemá základní třídu.  
  
 Dobrý Windows programování postupy vyžadují zobrazit čekání kurzoru, vždy, když provádíte operace, která přebírá znatelné množství času.  
  
 Počkejte kurzoru zobrazíte pouze definuje `CWaitCursor` proměnné před kód, který provádí náročná operace. Konstruktor objektu automaticky způsobí, že čekání kurzor, který se má zobrazit.  
  
 Při přechodu objekt mimo rozsah (na konci bloku, ve kterém `CWaitCursor` objekt deklarován), jeho destruktor nastaví kurzor na předchozí kurzor. Jinými slovy objekt provede nezbytné vyčištění automaticky.  
  
> [!NOTE]
>  Kvůli jejich konstruktory a destruktory fungování `CWaitCursor` objekty jsou vždy deklarované jako místní proměnné – nikdy deklarovány jako globální proměnné ani jsou budou přiděleny s **nové**.  
  
 Pokud provádíte operace, což by mohlo způsobit kurzor změnit, jako je například zobrazení okno se zprávou nebo dialogové okno, volání [obnovení](#restore) – členská funkce obnovení kurzor čekání. Je to v pořádku pro volání **obnovení** i při čekání kurzoru je aktuálně zobrazený.  
  
 Dalším způsobem zobrazíte kurzoru čekání je pomocí kombinace [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)a případně [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Ale `CWaitCursor` je jednodušší použít, protože nemusíte nastavte kurzor na předchozí kurzor, když jste hotovi s náročná operace.  
  
> [!NOTE]
>  Nastaví knihovny MFC a obnoví pomocí kurzor [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) virtuální funkce. Tato funkce vám umožňuje vlastní chování můžete přepsat.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CWaitCursor`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxwin.h  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]  
  
##  <a name="cwaitcursor"></a>  CWaitCursor::CWaitCursor  
 Počkejte kurzoru zobrazíte právě deklarovat `CWaitCursor` objekt před kód, který provádí náročná operace.  
  
```  
CWaitCursor();
```  
  
### <a name="remarks"></a>Poznámky  
 Konstruktor automaticky způsobí, že čekání kurzor, který se má zobrazit.  
  
 Při přechodu objekt mimo rozsah (na konci bloku, ve kterém `CWaitCursor` objekt deklarován), jeho destruktor nastaví kurzor na předchozí kurzor. Jinými slovy objekt provede nezbytné vyčištění automaticky.  
  
 Můžete využít výhod fakt, že destruktoru na konci bloku (který může být před ukončením funkce) na čekání kurzor aktivní pouze v části funkce. Tento postup je uveden v druhém níže uvedeném příkladu.  
  
> [!NOTE]
>  Kvůli jejich konstruktory a destruktory fungování `CWaitCursor` objekty jsou vždy deklarované jako místní proměnné – nikdy deklarovány jako globální proměnné, ani se jejich přidělený **nové**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]  
  
##  <a name="restore"></a>  CWaitCursor::Restore  
 Pokud chcete obnovit kurzor čekání, volejte tuto funkci po provedení operace, jako je například zobrazení okno se zprávou nebo dialogové okno, které mohou změnit kurzor čekání na jiný kurzor.  
  
```  
void Restore();
```  
  
### <a name="remarks"></a>Poznámky  
 Je možné volat **obnovení** i při čekání kurzor je aktuálně zobrazený.  
  
 Pokud potřebujete obnovit čekání kurzor v průběhu funkce než ten, ve kterém `CWaitCursor` je deklarován objekt, můžete volat [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)   
 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)   
 [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)   
 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)   
 [Jak se I: změnit myší v aplikaci Microsoft Foundation – třída](http://go.microsoft.com/fwlink/p/?linkid=128044)



