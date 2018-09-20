---
title: 'TN016: Použití knihovny MFC C++ vícenásobné dědičnosti | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.inheritance
dev_langs:
- C++
helpviewer_keywords:
- TN016
- MI (Multiple Inheritance)
- multiple inheritance, MFC support for
ms.assetid: 4ee27ae1-1410-43a5-b111-b6af9b84535d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c0ed5c1bc73f58bec1f9ad0d6a790fe3d3c0239
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444681"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: Použití vícenásobné dědičnosti jazyka C++ v prostředí MFC

Tato poznámka popisuje, jak pomocí Microsoft Foundation Classes vícenásobná dědičnost (IU). Použití MI se nevyžaduje s knihovnou MFC. MI není použit v jakékoli třídy knihovny MFC a není nutné psát knihovny tříd.

Následující dílčí témata popisují, jak MI ovlivňuje použití společné idiomy MFC a také některé z těchto omezení MI pokrývající. Některé z těchto omezení jsou obecné C++ omezením. Ostatní jsou uložené architektury MFC.

Na konci této Technická poznámka najdete kompletní aplikace knihovny MFC, která používá MI.

## <a name="cruntimeclass"></a>CRuntimeClass

Trvalost a mechanismy vytváření dynamických objektů použití knihovny MFC [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) datová struktura k jednoznačné identifikaci tříd. MFC jednu z těchto struktur přidruží každé dynamické a/nebo serializovatelné třídy ve vaší aplikaci. Tyto struktury jsou inicializovány při spuštění aplikace pomocí speciální statický objekt typu `AFX_CLASSINIT`.

Aktuální provádění `CRuntimeClass` nepodporuje MI informace typu za běhu. To neznamená, že MI nelze použít v aplikaci knihovny MFC. Při práci s objekty, které mají více než jedné základní třídy, ale bude mít některé odpovědnosti.

[CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) metoda nebude nesprávně určí typ objektu má více základních tříd. Proto nelze použít [CObject](../mfc/reference/cobject-class.md) jako virtuální základní třídy a všechna volání `CObject` členské funkce, jako například [CObject::Serialize](../mfc/reference/cobject-class.md#serialize) a [novéCObject::operator](../mfc/reference/cobject-class.md#operator_new)musí mít Kvalifikátory oboru, takže tento C++ můžete odstranit nejednoznačnost voláním příslušné funkce. Pokud program používá MI v rámci MFC, třídy, který obsahuje `CObject` základní třída musí být třída nejvíce vlevo v seznamu základních tříd.

Další možností je použít `dynamic_cast` operátor. Přetypování objekt se MI na jeden z jejích základních tříd vynutí kompilátoru použití funkcí v základní třídy zadané. Další informace najdete v tématu [dynamic_cast – operátor](../cpp/dynamic-cast-operator.md).

## <a name="cobject---the-root-of-all-classes"></a>CObject – kořenový všechny třídy

Všechny důležité třídy odvodit přímo nebo nepřímo ze třídy `CObject`. `CObject` nemá obsahují některé výchozí funkce však není nutné všechna data členů. Při použití MI vám bude obvykle dědit ze dvou nebo více `CObject`-odvozené třídy. Následující příklad ukazuje, jak třída může dědit z [CFrameWnd](../mfc/reference/cframewnd-class.md) a [coblist –](../mfc/reference/coblist-class.md):

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    // ...
};
CListWnd myListWnd;
```

V tomto případě `CObject` Přikládáme dvakrát. To znamená, že budete potřebovat způsob k rozlišení všechny odkazy na `CObject` operátory nebo metody. **Operátor new** a [operátor delete](../mfc/reference/cobject-class.md#operator_delete) jsou dva operátory, které musí být jednoznačně rozlišit. Další příklad – následující kód způsobí chybu v době kompilace:

```cpp
myListWnd.Dump(afxDump); // compile time error, CFrameWnd::Dump or CObList::Dump
```

## <a name="reimplementing-cobject-methods"></a>Reimplementing metody třídy CObject

Při vytváření novou třídu, která má dvě nebo více `CObject` odvozené základní třídy, byste měli znovu implementovat `CObject` metody, které chcete používání jiným lidem. Operátory **nové** a **odstranit** jsou povinné a [vypsat](../mfc/reference/cobject-class.md#dump) se doporučuje. Následující příklad reimplements **nové** a **odstranit** operátory a `Dump` metody:

```cpp
class CListWnd : public CFrameWnd, public CObList
{
public:
    void* operator new(size_t nSize)
    {
        return CFrameWnd:: operator new(nSize);
    }
    void operator delete(void* p)
    {
        CFrameWnd:: operator delete(p);
    }
    void Dump(CDumpContent& dc)
    {
        CFrameWnd::Dump(dc);
        CObList::Dump(dc);
    }
    // ...
};
```

## <a name="virtual-inheritance-of-cobject"></a>Virtuální dědičnost třídy CObject

To může zdát, že prakticky dědění `CObject` by vyřešit problém funkce nejednoznačnost, ale to není případ. Protože neexistuje žádná data členů v `CObject`, není nutné virtuální dědičnost, aby se zabránilo více kopií dat člena základní třídy. V prvním příkladu, které se zobrazilo dříve `Dump` virtuální metody je stále nejednoznačný, protože jinak v implementaci `CFrameWnd` a `CObList`. Nejlepší způsob, jak odstranit nejednoznačnost je postupujte podle doporučení v předchozí části.

## <a name="cobjectiskindof-and-run-time-typing"></a>CObject::IsKindOf a zadáním příkazu Run-Time

Za běhu psaní mechanismu, který podporuje knihovnu MFC ve `CObject` používá makra DECLARE_DYNAMIC, IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE, IMPLEMENT_DYNCREATE, DECLARE_SERIAL a IMPLEMENT_SERIAL. Tato makra lze provést kontrolu typu za běhu k zajištění bezpečné přetypování dolů.

Tato makra podporují pouze jednu základní třídu a bude fungovat v omezené způsob, jakým vícenásobně zděděné třídy. Základní třída, kterou zadáte v IMPLEMENT_DYNAMIC nebo IMPLEMENT_SERIAL by měla být základní třídy první (nebo úplně vlevo). Toto umístění vám umožní kontrolu pro základní třídu nejvíce vlevo pouze typu. Run-time typu systému vědět nic o dalších základních tříd. V následujícím příkladu se za běhu systémy provede kontrolu proti typu `CFrameWnd`, ale nic vědět o `CObList`.

```cpp
class CListWnd : public CFrameWnd, public CObList
{
    DECLARE_DYNAMIC(CListWnd)
    // ...
};
IMPLEMENT_DYNAMIC(CListWnd, CFrameWnd)
```

## <a name="cwnd-and-message-maps"></a>CWnd a mapy zpráv

Systém mapy zpráv knihovny MFC fungovala správně existují dva další požadavky:

- Musí obsahovat pouze jeden `CWnd`-odvozené základní třídy.

- `CWnd`-Odvozené základní třídy musí být základní třídy první (nebo úplně vlevo).

Tady jsou některé příklady, které nebudou fungovat:

```cpp
class CTwoWindows : public CFrameWnd, public CEdit
{ /* ... */ }; // error : two copies of CWnd

class CListEdit : public CObList, public CEdit
{ /* ... */ }; // error : CEdit (derived from CWnd) must be first
```

## <a name="a-sample-program-using-mi"></a>Ukázkový Program pomocí MI

Následující příklad je samostatná aplikace, která se skládá z jedné třídy odvozené od `CFrameWnd` a [CWinApp](../mfc/reference/cwinapp-class.md). Nedoporučujeme struktury aplikace tím, že toto je příklad nejmenší aplikace knihovny MFC, která má jednu třídu.

```cpp
#include <afxwin.h>

class CHelloAppAndFrame : public CFrameWnd, public CWinApp
{
public:
    CHelloAppAndFrame() {}

    // Necessary because of MI disambiguity
    void* operator new(size_t nSize)
        { return CFrameWnd::operator new(nSize); }
    void operator delete(void* p)
        { CFrameWnd::operator delete(p); }

    // Implementation
    // CWinApp overrides
    virtual BOOL InitInstance();
    // CFrameWnd overrides
    virtual void PostNcDestroy();
    afx_msg void OnPaint();

    DECLARE_MESSAGE_MAP()
};

BEGIN_MESSAGE_MAP(CHelloAppAndFrame, CFrameWnd)
    ON_WM_PAINT()
END_MESSAGE_MAP()

// because the frame window is not allocated on the heap, we must
// override PostNCDestroy not to delete the frame object
void CHelloAppAndFrame::PostNcDestroy()
{
    // do nothing (do not call base class)
}

void CHelloAppAndFrame::OnPaint()
{
    CPaintDC dc(this);
    CRect rect;
    GetClientRect(rect);

    CString s = "Hello, Windows!";
    dc.SetTextAlign(TA_BASELINE | TA_CENTER);
    dc.SetTextColor(::GetSysColor(COLOR_WINDOWTEXT));
    dc.SetBkMode(TRANSPARENT);
    dc.TextOut(rect.right / 2, rect.bottom / 2, s);
}

// Application initialization
BOOL CHelloAppAndFrame::InitInstance()
{
    // first create the main frame
    if (!CFrameWnd::Create(NULL, "Multiple Inheritance Sample",
        WS_OVERLAPPEDWINDOW, rectDefault))
        return FALSE;

    // the application object is also a frame window
    m_pMainWnd = this;
    ShowWindow(m_nCmdShow);
    return TRUE;
}

CHelloAppAndFrame theHelloAppAndFrame;
```

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
