---
title: 'TN016: Použití vícenásobné C++ dědičnosti MFC | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: cba37344a2d065c84e196330e3b4f9d859975102
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954855"
---
# <a name="tn016-using-c-multiple-inheritance-with-mfc"></a>TN016: Použití vícenásobné dědičnosti jazyka C++ v prostředí MFC
Tato poznámka popisuje, jak pomocí třídy Microsoft Foundation vícenásobná dědičnost (MI). Použití MI se nevyžaduje MFC. MI ještě není používáno ve všech tříd MFC a není nutné zapsat knihovny tříd.  
  
 Následující další části popisují, jak MI ovlivňuje použití běžné MFC idioms a také které se vztahuje některá omezení MI. Některé z těchto omezení jsou obecná omezení C++. Ostatní jsou způsobené architektury MFC.  
  
 Na konci této technické poznámky najdete kompletní MFC aplikace, která používá MI.  
  
## <a name="cruntimeclass"></a>CRuntimeClass  
 Trvalosti a mechanismy vytváření dynamických objektů MFC použití [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) struktura dat k jednoznačné identifikaci třídy. MFC přidružuje jednu z těchto struktur jednotlivé dynamické nebo serializovatelné třídy v aplikaci. Tyto struktury jsou inicializovány při spuštění aplikace s použitím speciální statické objektu typu `AFX_CLASSINIT`.  
  
 Aktuální implementace `CRuntimeClass` nepodporuje MI informací o typu modulu runtime. To neznamená, že MI nelze použít v aplikaci MFC. Při práci s objekty, které mají více než jedné základní třídy, ale bude mít určité odpovědnosti.  
  
 [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof) metoda nebude určit správně typ objektu má vícenásobné základní třídy. Proto nelze použít [CObject](../mfc/reference/cobject-class.md) jako virtuální základní třídy a všechny volání `CObject` členské funkce, jako [CObject::Serialize](../mfc/reference/cobject-class.md#serialize) a [novéCObject::operator](../mfc/reference/cobject-class.md#operator_new)musí mít obor kvalifikátory tak, že C++ můžete odstranit nejednoznačnost volání příslušné funkce. Používá-li program MI v rámci MFC, třídu, která obsahuje `CObject` základní třída musí být třída nejvíce vlevo v seznamu základní třídy.  
  
 Další možností je použít `dynamic_cast` operátor. Přetypování objekt se MI na jeden z jeho základních tříd vynutí kompilátoru použití funkcí v zadané základní třídě. Další informace najdete v tématu [dynamic_cast – operátor](../cpp/dynamic-cast-operator.md).  
  
## <a name="cobject---the-root-of-all-classes"></a>CObject – kořenovém všechny třídy  
 Všechny třídy významné odvozena od třídy přímo nebo nepřímo `CObject`. `CObject` neobsahuje žádná data člena, ale nemá některé výchozí funkce. Při použití MI bude obvykle dědění ze dvou nebo více `CObject`-odvozených třídách. Následující příklad ilustruje, jak můžete třídy dědí [CFrameWnd](../mfc/reference/cframewnd-class.md) a [CObList](../mfc/reference/coblist-class.md):  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
 ...  
};  
CListWnd myListWnd;  
```  
  
 V takovém případě `CObject` je součástí dvakrát. To znamená, že budete potřebovat způsob k rozlišení všechny odkazy na `CObject` metody nebo operátory. **New – operátor** a [delete – operátor](../mfc/reference/cobject-class.md#operator_delete) jsou dva operátory, které musí jednoznačně rozlišit. Například následující kód způsobí chybu v době kompilace:  
  
```  
myListWnd.Dump(afxDump);
*// compile time error, CFrameWnd::Dump or CObList::Dump   
```  
  
## <a name="reimplementing-cobject-methods"></a>Reimplementing metody CObject  
 Když vytvoříte novou třídu, která má dva nebo více `CObject` odvozené třídy base měli přeimplementovat `CObject` metody, které chcete ostatním používat. Operátory **nové** a **odstranit** jsou povinné a [Dump](../mfc/reference/cobject-class.md#dump) se doporučuje. Následující příklad reimplements **nové** a **odstranit** operátory a `Dump` metoda:  
  
```  
class CListWnd : public CFrameWnd, public CObList  
{  
public:  
    void* operator new(size_t nSize)  
 { return CFrameWnd:: operator new(nSize);

}  
    void operator delete(void* p)  
 { CFrameWnd:: operator delete(p);

}  
 
    void Dump(CDumpContent& dc)  
 { CFrameWnd::Dump(dc);

    CObList::Dump(dc);

} 
 ...  
};  
```  
  
## <a name="virtual-inheritance-of-cobject"></a>Virtuální dědičnost CObject  
 Zdát, že prakticky dědění `CObject` by vyřešen nejednoznačnosti funkce, ale které se nevztahuje na případ. Vzhledem k tomu, že neexistují žádná data člena v `CObject`, není nutné virtuální dědičnost, aby se zabránilo více kopií dat člena třídy base. V prvním příkladu, která byla dříve, zobrazí `Dump` virtuální metoda je stále nejednoznačné, protože je implementována jinak v `CFrameWnd` a `CObList`. Nejlepší způsob, jak odebrat nejednoznačnosti je postupujte podle doporučení uvedená v předchozí části.  
  
## <a name="cobjectiskindof-and-run-time-typing"></a>CObject::IsKindOf a zadáte běhu  
 Zadáním mechanismus běhu nepodporuje MFC v `CObject` používá DECLARE_DYNAMIC, implement_dynamic –, DECLARE_DYNCREATE –, IMPLEMENT_DYNCREATE, declare_serial – a implement_serial – makra. Tyto makra můžete provést kontrolu typu běhu k zajištění bezpečného downcasts.  
  
 Tyto makra podporují pouze jediná základní třída a bude fungovat v omezené míře pro násobkem zděděné třídy. Základní třídy, které zadáte v implement_dynamic – nebo implement_serial – musí být základní třídy první (nebo nejvíce vlevo). Toto umístění vám umožní kontrola pro základní třídu nejvíce vlevo pouze typu. Systém typů běhu vědět nic o další základní třídy. V následujícím příkladu, systémy běhu provede kontrolu proti typu `CFrameWnd`, ale nic vědět o `CObList`.  
  
```  
class CListWnd : public CFrameWnd,
    public CObList  
{  
    DECLARE_DYNAMIC(CListWnd) 
 ...  
};  
IMPLEMENT_DYNAMIC(CListWnd,
    CFrameWnd)  
```  
  
## <a name="cwnd-and-message-maps"></a>CWnd a mapy zpráv  
 Pro systém mapy zpráv knihovny MFC fungovala správně existují dva další požadavky:  
  
-   Musí existovat jenom jeden `CWnd`-odvozené základní třídy.  
  
-   `CWnd`-Odvozené třídy základní musí být základní třídy první (nebo nejvíce vlevo).  
  
 Zde jsou některé příklady, které nebudou fungovat:  
  
```  
class CTwoWindows : public CFrameWnd,
    public CEdit  
 { ... }; *// error : two copies of CWnd  
 
class CListEdit : public CObList,
    public CEdit  
 { ... }; *// error : CEdit (derived from CWnd) must be first  
```  
  
## <a name="a-sample-program-using-mi"></a>Ukázka programu pomocí MI  
 Následující příklad je samostatná aplikace, která se skládá z jedné třídy odvozené od `CFrameWnd` a [CWinApp](../mfc/reference/cwinapp-class.md). Nedoporučujeme struktury aplikace tímto způsobem, že toto je příklad nejmenší MFC aplikace, která obsahuje jednu třídu.  
  
```  
#include <afxwin.h>  
  
class CHelloAppAndFrame : public CFrameWnd, public CWinApp  
{   
public:  
    CHelloAppAndFrame()  
        { }  
  
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
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

