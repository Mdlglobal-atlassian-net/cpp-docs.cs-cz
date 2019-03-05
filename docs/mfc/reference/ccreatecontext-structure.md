---
title: Ccreatecontext – struktura
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: f84c0da7530a774ebe2b33aea0bddc5b0bf0fe17
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326345"
---
# <a name="ccreatecontext-structure"></a>Ccreatecontext – struktura

Rozhraní používá `CCreateContext` struktury při vytváření oken s rámečkem a zobrazení, které jsou spojené s dokumentem.

## <a name="syntax"></a>Syntaxe

```
struct CCreateContext
```

## <a name="remarks"></a>Poznámky

`CCreateContext` Struktura a nemá žádné základní třídy.

Při vytváření okna hodnoty v této struktuře poskytují informace použité pro připojení komponenty dokument k zobrazení jeho data. Budete muset použít `CCreateContext` Pokud přepíšete součástí procesu vytváření.

A `CCreateContext` struktura obsahuje odkazy na dokument, okno rámce, zobrazení a šablony dokumentu. Také obsahuje ukazatel `CRuntimeClass` , který určuje typ zobrazení vytvořit. Informace o třídě za běhu a ukazatel na aktuální dokument slouží k vytvoření nového zobrazení dynamicky. Následující tabulce najdete doporučení, jak a kdy každý `CCreateContext` člena může použít:

|Člen|Typ|Co je pro|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` k vytvoření nového zobrazení.|
|`m_pCurrentDoc`|`CDocument*`|K existujícímu dokumentu, který se má přidružit nové zobrazení.|
|`m_pNewDocTemplate`|`CDocTemplate*`|Šablona dokumentu přidružené k vytvoření nového okna rámce MDI.|
|`m_pLastView`|`CView*`|Původní zobrazení, ve kterém jsou modelovány další zobrazení, stejně jako v vytváření rozdělovač okna zobrazení nebo vytvoření druhého zobrazení dokumentu.|
|`m_pCurrentFrame`|`CFrameWnd*`|Okno rámce, ve kterém jsou modelovány další okna s rámečkem, stejně jako v vytvoření druhého okna rámce dokumentu.|

Když šablony dokumentu vytvoří dokument a jeho přidružených součásti, ověří informace uložené v `CCreateContext` struktury. Například by neměl vytvořit zobrazení pro neexistující dokumentu.

> [!NOTE]
>  Všechny ukazatele v `CCreateContext` jsou volitelné a může být `NULL` Pokud neurčené nebo neznámý.

`CCreateContext` používá členské funkce uvedené v části "Viz také." Pokud chcete je přepsat najdete konkrétní informace popisy těchto funkcí.

Tady je pár obecné pokyny:

- Pokud je předán jako argument pro vytvoření okna, stejně jako v `CWnd::Create`, `CFrameWnd::Create`, a `CFrameWnd::LoadFrame`, vytvořit kontext určuje, co nového okna musí být připojené k. Pro většinu windows celá struktura je volitelné a `NULL` lze předat ukazatele.

- Přepisovatelné členské funkce jako například `CFrameWnd::OnCreateClient`, `CCreateContext` argument je nepovinný.

- Pro členské funkce, které jsou zahrnuté v zobrazení vytváření, musíte zadat dostatek informací pro vytvoření zobrazení. Pro zobrazení první okno s rozdělovačem. musíte například zadat informace o zobrazení třídy a aktuální dokument.

Obecně platí, pokud použijete výchozí nastavení rozhraní framework, můžete ignorovat `CCreateContext`. Pokud se pokusíte pokročilejší úpravy, zdrojový kód knihovny Microsoft Foundation Class nebo ukázkové programy, jako je například VIEWEX, vás provede. Pokud zapomenete povinný parametr, kontrolní výraz framework říct, co jste zapomněli.

Další informace o `CCreateContext`, najdete v ukázce MFC [VIEWEX](../../visual-cpp-samples.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
