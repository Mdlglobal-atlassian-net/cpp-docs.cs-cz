---
title: 'TN039: MFC OLE – implementace automatizace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c6475e8c259026618192489ac2c67c20ed03d92
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385336"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039: MFC/OLE – implementace automatizace
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
## <a name="overview-of-ole-idispatch-interface"></a>Přehled OLE IDispatch – rozhraní  
 `IDispatch` Rozhraní je prostředek, pomocí kterého aplikace vystavit metody a vlastnosti, které další aplikace, jako je například Visual BASIC nebo jiných jazyků, můžete provést pomocí funkcí aplikace. Je nejdůležitější část tohoto rozhraní **volání metody IDispatch::Invoke** funkce. MFC používá "mapy odesílání" implementovat **volání metody IDispatch::Invoke**. Mapy odesílání poskytuje informace implementace MFC rozložení nebo "tvaru" z vaší `CCmdTarget`-odvozené třídy, tak, aby ho můžete přímo upravit vlastnosti objektu nebo volat členské funkce v rámci objektu vyhovět  **Volání metody IDispatch::Invoke** požadavky.  
  
 Ve většině případů ClassWizard a MFC spolupracovat a skrýt většinu podrobnosti o OLE – automatizace z programátorů aplikace. Programátorů soustřeďuje na funkce skutečného vystavit v aplikaci a nemá si dělat starosti základní vložení.  
  
 Existují případy, ale pokud je nezbytné zjistit, co MFC probíhá na pozadí. Tato poznámka vyřeší tom, jak rozhraní přiřadí **DISPID**s členské funkce a vlastnosti. Znalostní báze algoritmu MFC používá pro přiřazení **DISPID**s je potřeba, pouze když potřebujete vědět, ID, například při vytváření knihovnu"typ" pro objekty vaší aplikace.  
  
## <a name="mfc-dispid-assignment"></a>Přiřazení MFC DISPID  
 I když se koncový uživatel automatizace (Visual Basic uživatel, např.), se zobrazí skutečné názvy automatizace povolené vlastnosti a metody v jejich kódu (například objektu vývoz. ShowWindow), provádění **volání metody IDispatch::Invoke** neobdrží skutečné názvy. Z důvodů optimalizace, obdrží **DISPID**, což je 32-bit "magic souboru cookie" popisující metody nebo vlastnosti, která je přístupná. Tyto **DISPID** hodnoty jsou vráceny z `IDispatch` implementace prostřednictvím jinou metodu, s názvem **funkce IDispatch::GetIDsOfNames**. Automatizace aplikace klienta bude volat `GetIDsOfNames` po pro každý člen nebo vlastnost hodlá přístup a je do mezipaměti pro pozdější volání **volání metody IDispatch::Invoke**. Tímto způsobem je nákladné řetězec vyhledávání je možné pouze jednou za použití objektu místo jednou za **volání metody IDispatch::Invoke** volání.  
  
 Určuje MFC **DISPID**s pro každý metod a vlastností podle dvě věci:  
  
-   Vzdálenost od začátku expediční mapy (1 relativní)  
  
-   Vzdálenost od nejvíce odvozené třídy (0 relativní) mapy odesílání  
  
 **DISPID** je rozdělena na dva oddíly. **LOWORD** z **DISPID** obsahuje první součást, vzdálenost od začátku expediční mapy. **HIWORD** obsahuje vzdálenost od nejvíce odvozené třídy. Příklad:  
  
```  
class CDispPoint : public CCmdTarget  
{  
public:  
    short m_x,
    m_y;  
 ...  
    DECLARE_DISPATCH_MAP() 
 ...  
};  
 
class CDisp3DPoint : public CDispPoint  
{  
public:  
    short m_z;  
 ...  
    DECLARE_DISPATCH_MAP() 
 ...  
};  
 
BEGIN_DISPATCH_MAP(CDispPoint,
    CCmdTarget)  
    DISP_PROPERTY(CDispPoint, "x",
    m_x,
    VT_I2)  
    DISP_PROPERTY(CDispPoint, "y",
    m_y,
    VT_I2)  
END_DISPATCH_MAP()  
 
BEGIN_DISPATCH_MAP(CDisp3DPoint,
    CDispPoint)  
    DISP_PROPERTY(CDisp3DPoint, "z",
    m_z,
    VT_I2)  
END_DISPATCH_MAP()  
```  
  
 Jak vidíte, existují dvě třídy, které zveřejňují rozhraní automatizace OLE. Jedna z těchto tříd je odvozený z jiných a proto využívá funkce základní třídy, včetně část automatizace OLE ("x" a "y" vlastnosti v tomto případě).  
  
 MFC vygeneruje **DISPID**s pro třídy CDispPoint následujícím způsobem:  
  
```  
property X    (DISPID)0x00000001  
property Y    (DISPID)0x00000002  
```  
  
 Vzhledem k tomu, že vlastnosti nejsou v základní třídě, **HIWORD** z **DISPID** je vždy nula (vzdálenost od nejvíce odvozené třídy pro CDispPoint je nulová).  
  
 MFC vygeneruje **DISPID**s pro třídy CDisp3DPoint následujícím způsobem:  
  
```  
property Z    (DISPID)0x00000001  
property X    (DISPID)0x00010001  
property Y    (DISPID)0x00010002  
```  
  
 Je zadána vlastnost Z **DISPID** s nulou **HIWORD** vzhledem k tomu, že je definována ve třídě, která je vystavení vlastností CDisp3DPoint. Vzhledem k tomu, že vlastnosti X a Y jsou definovány v základní třídě, **HIWORD** z **DISPID** je 1, protože třída, ve kterém jsou definovány tyto vlastnosti je ve vzdálenosti jeden odvození od nejvíce odvozené třídy.  
  
> [!NOTE]
>  **LOWORD** je vždy určen pozici v mapě, i pokud existuje položky v mapě s explicitní **DISPID** (Další informace naleznete na **_ID** verze `DISP_PROPERTY` a `DISP_FUNCTION` makra).  
  
## <a name="advanced-mfc-dispatch-map-features"></a>Pokročilé funkce mapy odesílání MFC  
 Existuje mnoho dalších funkcí, které ClassWizard nepodporuje tato verze aplikace Visual C++. Podporuje ClassWizard `DISP_FUNCTION`, `DISP_PROPERTY`, a `DISP_PROPERTY_EX` která definují, metoda, vlastnost proměnné člena a vlastnost člena funkce get nebo nastavení, v uvedeném pořadí. Tyto možnosti jsou obvykle všechno, co je potřeba k vytvoření většina automatizační servery.  
  
 Následující další makra lze použít, pokud nejsou adekvátní makra ClassWizard podporována: `DISP_PROPERTY_NOTIFY`, a `DISP_PROPERTY_PARAM`.  
  
## <a name="disppropertynotify--macro-description"></a>Disp_property_notify – – Popis makro  
  
```  
 
    DISP_PROPERTY_NOTIFY(
 theClass,   
    pszName, 
    memberName, 
    pfnAfterSet, 
    vtPropType) 
```  
  
## <a name="remarks"></a>Poznámky  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 `pszName`  
 Externí název vlastnosti.  
  
 `memberName`  
 Název členské proměnné, ve kterém je uložený vlastnost.  
  
 `pfnAfterSet`  
 Název členské funkce k volání při změně vlastnosti.  
  
 `vtPropType`  
 Hodnota určující typ vlastnosti.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro je podobné jako u `DISP_PROPERTY`kromě toho, že ho přijme další argument. Další argument *pfnAfterSet,* by měla být členské funkce, která nic a nepřijímá žádné parametry, void OnPropertyNotify()'. Bude volána **po** změnil členské proměnné.  
  
## <a name="disppropertyparam--macro-description"></a>Disp_property_param – – Popis makro  
  
```  
 
    DISP_PROPERTY_PARAM(
 theClass,   
    pszName, 
    pfnGet, 
    pfnSet, 
    vtPropType, 
    vtsParams) 
```  
  
## <a name="remarks"></a>Poznámky  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 `pszName`  
 Externí název vlastnosti.  
  
 `memberGet`  
 Název členské funkce používá GET pro vlastnost.  
  
 `memberSet`  
 Název členské funkce lze nastavit vlastnost.  
  
 `vtPropType`  
 Hodnota určující typ vlastnosti.  
  
 `vtsParams`  
 Řetězec místa oddělené VTS_ pro jednotlivé parametry.  
  
## <a name="remarks"></a>Poznámky  
 Podobně jako `DISP_PROPERTY_EX` makro, tento makro definuje vlastnost přístupný pomocí samostatných Get a Set členské funkce. Toto makro, můžete však zadat seznam parametrů pro vlastnost. To je užitečné pro implementaci vlastnosti, které jsou indexované nebo parametry jiným způsobem. Parametry budou vždy umístěny nejprve, za nímž následuje novou hodnotu pro vlastnost. Příklad:  
  
```  
DISP_PROPERTY_PARAM(CMyObject, "item",
    GetItem,
    SetItem,
    VT_DISPATCH,
    VTS_I2 VTS_I2)  
```  
  
 by odpovídat k získání a nastavení členské funkce:  
  
```  
LPDISPATCH CMyObject::GetItem(short row,
    short col)  
void CMyObject::SetItem(short row,
    short col,
    LPDISPATCH newValue)  
```  
  
## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID – Popisy makro  
  
```  
 
    DISP_FUNCTION_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnMember, 
    vtRetVal, 
    vtsParams)DISP_PROPERTY_ID(
 theClass,   
    pszName, 
    dispid, 
    memberName, 
    vtPropType)DISP_PROPERTY_NOTIFY_ID(
 theClass,   
    pszName, 
    dispid, 
    memberName, 
    pfnAfterSet, 
    vtPropType)DISP_PROPERTY_EX_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnGet, 
    pfnSet, 
    vtPropType)DISP_PROPERTY_PARAM_ID(
 theClass,   
    pszName, 
    dispid, 
    pfnGet, 
    pfnSet, 
    vtPropType, 
    vtsParams) 
```  
  
## <a name="remarks"></a>Poznámky  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 Název třídy.  
  
 `pszName`  
 Externí název vlastnosti.  
  
 `dispid`  
 Opravené DISPID pro vlastnosti nebo metody.  
  
 `pfnGet`  
 Název členské funkce používá GET pro vlastnost.  
  
 `pfnSet`  
 Název členské funkce lze nastavit vlastnost.  
  
 `memberName`  
 Název členské proměnné pro mapování pro vlastnost  
  
 `vtPropType`  
 Hodnota určující typ vlastnosti.  
  
 `vtsParams`  
 Řetězec místa oddělené VTS_ pro jednotlivé parametry.  
  
## <a name="remarks"></a>Poznámky  
 Tyto makra umožňují zadat **DISPID** místo MFC automaticky přiřadit jeden. Tato upřesňující makra mají stejné názvy s tím rozdílem, že ID je připojeným k názvu – makro (například **DISP_PROPERTY_ID**) a ID je dáno parametr pouze po zadaný `pszName` parametr. V tématu AFXDISP. H Další informace o těchto makra. **_ID** položky musí být umístěna na konci mapy odesílání. Ovlivňují automatického **DISPID** generování stejným způsobem jako jinou hodnotu než **_ID** by verzi makro ( **DISPID**s vyplývají z pozice). Příklad:  
  
```  
BEGIN_DISPATCH_MAP(CDisp3DPoint,
    CCmdTarget)  
    DISP_PROPERTY(CDisp3DPoint, "y",
    m_y,
    VT_I2)  
    DISP_PROPERTY(CDisp3DPoint, "z",
    m_z,
    VT_I2)  
    DISP_PROPERTY_ID(CDisp3DPoint, "x",
    0x00020003,
    m_x,
    VT_I2)  
END_DISPATCH_MAP()  
```  
  
 MFC vygeneruje hodnoty dispID pro třídu CDisp3DPoint následujícím způsobem:  
  
```  
property X    (DISPID)0x00020003  
property Y    (DISPID)0x00000002  
property Z     (DISPID)0x00000001  
```  
  
 Určení pevná **DISPID** je užitečná k zachování zpětné kompatibility na dříve existující rozhraní dispatch, nebo k implementaci určitých definovaná systémem metody nebo vlastnosti (obvykle označený jako záporné  **DISPID**, například **DISPID_NEWENUM** kolekce).  
  
#### <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>Načítání IDispatch rozhraní pro COleClientItem  
 Mnoho serverů, budou podporovat automatizace v rámci jejich dokumentu objekty, spolu s funkcí serveru OLE. Chcete-li získat přístup k tomuto rozhraní automatizace, je potřeba přístup přímo **COleClientItem::m_lpObject** členské proměnné. Následující kód načte `IDispatch` rozhraní pro objekt odvozené z `COleClientItem`. Pokud zjistíte, tato funkce nezbytné, může zahrnovat kód pod ve vaší aplikaci:  
  
```  
LPDISPATCH CMyClientItem::GetIDispatch()  
{  
    ASSERT_VALID(this);

 ASSERT(m_lpObject != NULL);

 
    LPUNKNOWN lpUnk = m_lpObject;  
 
    Run();
*// must be running  
 
    LPOLELINK lpOleLink = NULL;  
    if (m_lpObject->QueryInterface(IID_IOleLink,   
 (LPVOID FAR*)&lpOleLink) == NOERROR)  
 {  
    ASSERT(lpOleLink != NULL);

    lpUnk = NULL;  
    if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)  
 {  
    TRACE0("Warning: Link is not connected!\n");

    lpOleLink->Release();
return NULL;  
 }  
    ASSERT(lpUnk != NULL);

 }  
 
    LPDISPATCH lpDispatch = NULL;  
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch)   
 != NOERROR)  
 {  
    TRACE0("Warning: does not support IDispatch!\n");

    return NULL;  
 }  
 
    ASSERT(lpDispatch != NULL);

    return lpDispatch;  
}  
```  
  
 Rozhraní dispatch vrácená této funkce pak může použít přímo nebo připojený k `COleDispatchDriver` pro typově bezpečný přístup. Pokud ho používáte přímo, ujistěte se, že zavoláte jeho **verze** člen při prostřednictvím pomocí ukazatele ( `COleDispatchDriver` destruktor k tomu ve výchozím nastavení).  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

