---
title: Struktura CRuntimeClass | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e36baac5850942239bc9e553ed041a2914f8d670
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079541"
---
# <a name="cruntimeclass-structure"></a>Struktura CRuntimeClass
Jednotlivé třídy odvozené od `CObject` je přidružen `CRuntimeClass` struktura, která můžete použít k získání informací o objektu nebo její základní třída za běhu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct CRuntimeClass  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRuntimeClass::CreateObject](#createobject)|Vytvoří objekt při běhu.|  
|[CRuntimeClass::FromName](#fromname)|Vytvoří objekt při běhu pomocí názvu třídy známé.|  
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Určuje, pokud třída je odvozený od pro zadanou třídu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Název třídy.|  
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Velikost objektu v bajtech.|  
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Ukazatel `CRuntimeClass` struktura základní třídy.|  
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Ukazatel na funkci, která dynamicky vytvoří objekt.|  
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Vrátí `CRuntimeClass` struktury (pouze k dispozici, pokud dynamicky propojené).|  
|[CRuntimeClass::m_wSchema](#m_wschema)|Číslo schématu třídy.|  
  
## <a name="remarks"></a>Poznámky  
 `CRuntimeClass` je struktura a proto nemá základní třídu.  
  
 Možnost určit třídu objektu v době běhu je užitečné, když je potřeba další typ kontroly argumenty funkce, nebo když musíte napsat kód speciální na základě třídy objektu. Run-time třída informace nepodporují přímo jazyka C++.  
  
 `CRuntimeClass` poskytuje informace o související objekt C++, jako je například ukazatel `CRuntimeClass` základní třídy a název třídy ASCII související třídy. Tato struktura je navíc implementovaná různé funkce, které lze vytvořit dynamicky objekty, určení typu objektu pomocí názvu obeznámeni, a určení, pokud je související třída odvozená z určité třídy.  
  
 Další informace o používání `CRuntimeClass`, najdete v článku [informace o třídě přístup k Run-Time](../../mfc/accessing-run-time-class-information.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CRuntimeClass`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="createobject"></a>  CRuntimeClass::CreateObject  
 Volání této funkce pro zadanou třídu vytvořit dynamicky za běhu.  
  
```  
CObject* CreateObject();  
  
static CObject* PASCAL CreateObject(LPCSTR lpszClassName);  
  
static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszClassName*  
 Známé název třídy, který se má vytvořit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově vytvořený objekt nebo **NULL** Pokud název třídy nebyl nalezen nebo není dostatek paměti k vytvoření objektu.  
  
### <a name="remarks"></a>Poznámky  
 Třídy odvozené od `CObject` může podporovat dynamické vytváření, což je možnost vytvořit objekt zadané třídy v době běhu. Dokumentu, zobrazení a rámečku třídy, například by měly podporovat dynamického vytváření. Další informace o dynamické vytváření a `CreateObject` člena, najdete v části [CObject – třída](../../mfc/using-cobject.md) a [CObject – třída: určení úrovní funkčnosti](../../mfc/specifying-levels-of-functionality.md).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="fromname"></a>  CRuntimeClass::FromName  
 Volání této funkce můžete získat `CRuntimeClass` struktura přidružené k názvu seznámit.  
  
```  
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);  
  
static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszClassName*  
 Známé název třídy odvozené od `CObject`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `CRuntimeClass` objekt, odpovídající název jako předaný v *lpszClassName*. Funkce vrátí hodnotu **NULL** Pokud nebyl nalezen žádný odpovídající název třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]  
  
##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom  
 Volání této funkce k určení, pokud je volání třída odvozená z třídy zadané v *pBaseClass* parametr.  
  
```  
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;

 
```  
  
### <a name="parameters"></a>Parametry  
 *pBaseClass*  
 Známé název třídy odvozené od `CObject`.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud třída volání `IsDerivedFrom` je odvozený od základní třídy, jehož `CRuntimeClass` struktura je daný jako parametr; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Relace je určen podle "proti" ze člena třídy řetězem odvozených tříd úplně k nejvyšší. Tato funkce vrátí pouze **FALSE** Pokud není nalezena žádná shoda pro základní třídy.  
  
> [!NOTE]
>  Použít `CRuntimeClass` strukturu, musíte zahrnout implement_dynamic –, IMPLEMENT_DYNCREATE nebo implement_serial – makro implementace třídy, pro který chcete načíst informace o běhu objektu.  
  
 Další informace o používání `CRuntimeClass`, najdete v článku [CObject – třída: informace o třídě přístup k Run-Time](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]  
  
##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName  
 Ukončené hodnotou null řetězec obsahující název třídy ASCII.  
  
### <a name="remarks"></a>Poznámky  
 Tento název slouží k vytvoření instance třídy pomocí `FromName` – členská funkce.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize  
 Velikost objektu v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 Pokud objekt má datových členů, které odkazují na přidělenou paměť, velikost paměti, že není součástí.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass  
 Pokud vaše aplikace staticky odkazuje na knihovny MFC a tento – datový člen obsahuje odkazy `CRuntimeClass` struktura základní třídy.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace dynamicky odkazuje na knihovny MFC, najdete v části [m_pfnGetBaseClass](#m_pfngetbaseclass).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject  
 Ukazatel na výchozí konstruktor, který vytvoří objekt vaší třídy.  
  
### <a name="remarks"></a>Poznámky  
 Tento ukazatel je platná pouze v případě třída podporuje dynamické vytvoření; jinak, funkce vrátí hodnotu **NULL**.  
  
##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass  
 Pokud vaše aplikace používá knihovny MFC jako sdílenou knihovnu DLL, tento člen dat odkazuje na funkci, která vrátí `CRuntimeClass` struktura základní třídy.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vaše aplikace staticky odkazuje na knihovny MFC, najdete v části [m_pBaseClass](#m_pbaseclass).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema  
 Číslo schématu (-1 pro třídy nonserializable).  
  
### <a name="remarks"></a>Poznámky  
 Další informace o schématu čísla najdete v tématu [implement_serial –](run-time-object-model-services.md#implement_serial) makro.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [IsDerivedFrom](#isderivedfrom).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)   
 [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)   
 [RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)   
 [IMPLEMENT_DYNAMIC –](run-time-object-model-services.md#implement_dynamic)   
 [IMPLEMENT_DYNCREATE –](run-time-object-model-services.md#implement_dyncreate)   
 [IMPLEMENT_SERIAL –](run-time-object-model-services.md#implement_serial)



