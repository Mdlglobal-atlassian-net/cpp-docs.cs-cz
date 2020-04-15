---
title: CCreateContext – struktura
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 29fc6210b9888b6a5ba5aaf15b66242c29c15dc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369383"
---
# <a name="ccreatecontext-structure"></a>CCreateContext – struktura

Rámec používá `CCreateContext` strukturu při vytváření oken rámců a zobrazení, které jsou přidruženy k dokumentu.

## <a name="syntax"></a>Syntaxe

```
struct CCreateContext
```

## <a name="remarks"></a>Poznámky

`CCreateContext`je struktura a nemá základní třídu.

Při vytváření okna poskytují hodnoty v této struktuře informace použité k připojení součástí dokumentu k zobrazení jeho dat. Je třeba použít `CCreateContext` pouze v případě, že jsou přepsání části procesu vytváření.

Struktura `CCreateContext` obsahuje ukazatele na dokument, okno rámce, zobrazení a šablonu dokumentu. Obsahuje také ukazatel na, `CRuntimeClass` který identifikuje typ zobrazení, které chcete vytvořit. Informace o třídě za běhu a aktuální ukazatel dokumentu se používají k dynamickému vytvoření nového zobrazení. Následující tabulka uvádí, jak `CCreateContext` a kdy může být každý člen použit:

|Člen|Typ|K čemu je|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`nového zobrazení, které chcete vytvořit.|
|`m_pCurrentDoc`|`CDocument*`|Existující dokument, který má být přidružen k novému zobrazení.|
|`m_pNewDocTemplate`|`CDocTemplate*`|Šablona dokumentu přidružená k vytvoření nového okna rámce MDI.|
|`m_pLastView`|`CView*`|Původní pohled, ve kterém jsou modelovány další pohledy, jako při vytváření pohledů rozdělovače oken nebo při vytváření druhého pohledu v dokumentu.|
|`m_pCurrentFrame`|`CFrameWnd*`|Okno rámce, ve kterém jsou modelována další okna rámců, jako při vytváření druhého okna rámce v dokumentu.|

Když šablona dokumentu vytvoří dokument a jeho přidružené součásti, `CCreateContext` ověří informace uložené ve struktuře. Zobrazení by například nemělo být vytvořeno pro neexistující dokument.

> [!NOTE]
> Všechny ukazatele v `CCreateContext` jsou volitelné a `NULL` může být, pokud není zadán nebo neznámý.

`CCreateContext`je používán členskými funkcemi uvedenými v části "Viz také". Konkrétní informace naleznete v popisech těchto funkcí, pokud je chcete přepsat.

Zde je několik obecných pokynů:

- Při předání jako argument pro vytvoření `CWnd::Create` `CFrameWnd::Create`okna, `CFrameWnd::LoadFrame`jako v , , a , vytvořit kontext určuje, co nové okno by mělo být připojeno k. Pro většinu oken je volitelná `NULL` celá struktura a lze předat ukazatel.

- Pro overridable členské funkce, `CCreateContext` jako je například `CFrameWnd::OnCreateClient`argument je volitelné.

- Pro členské funkce, které jsou součástí vytváření zobrazení, je nutné poskytnout dostatek informací k vytvoření zobrazení. Například pro první zobrazení v okně rozdělovače je nutné zadat informace o třídě zobrazení a aktuální doklad.

Obecně platí, že pokud použijete výchozí `CCreateContext`hodnoty rozhraní, můžete ignorovat . Pokud se pokusíte o pokročilejší úpravy, provede vás zdrojový kód knihovny tříd Microsoft Foundation nebo ukázkové programy, například VIEWEX. Pokud zapomenete požadovaný parametr, kontrolní výraz rámce vám řekne, co jste zapomněli.

Další informace `CCreateContext`naleznete v tématu výběrová analýza knihovny [MFC VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Vytvořit](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Vytvořit](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Vytvořit](../../mfc/reference/cwnd-class.md#create)
