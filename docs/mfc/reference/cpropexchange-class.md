---
title: Cpropexchange – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
dev_langs:
- C++
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8b63de74a044a55362c2ebafc814fcf0136434d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216839"
---
# <a name="cpropexchange-class"></a>Cpropexchange – třída
Podporuje implementaci persistence pro ovládací prvky OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE CPropExchange  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPropExchange::ExchangeBlobProp](#exchangeblobprop)|Vymění vlastnost binárních rozsáhlých objektů (BLOB).|  
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|Vymění vlastnosti font.|  
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|Vymění vlastnost ovládací prvek a do souboru.|  
|[CPropExchange::ExchangeProp](#exchangeprop)|Vymění vlastnosti všech předdefinovaných typů.|  
|[CPropExchange::ExchangeVersion](#exchangeversion)|Vymění číslo verze ovládacího prvku OLE.|  
|[CPropExchange::GetVersion](#getversion)|Získá číslo verze ovládacího prvku OLE.|  
|[CPropExchange::IsAsynchronous](#isasynchronous)|Určuje, pokud jsou vlastnost výměny provádět asynchronně.|  
|[CPropExchange::IsLoading](#isloading)|Určuje, jestli se vlastnosti do ovládacího prvku načtení nebo uložení z něj.|  
  
## <a name="remarks"></a>Poznámky  
 `CPropExchange` nemá základní třídu.  
  
 Vytvoří kontext a směr vlastnost exchange.  
  
 Trvalost je exchange informace o stavu ovládacího prvku, obvykle reprezentováno vlastnostmi až střední samotný ovládací prvek.  
  
 Vytvoří objekt, odvozený z rozhraní framework `CPropExchange` při je oznámeno, že vlastnosti ovládacího prvku OLE mají být načteny z nebo uložené do trvalého úložiště.  
  
 Rozhraní framework předává ukazatel na tuto `CPropExchange` objekt ovládacího prvku `DoPropExchange` funkce. Pokud jste použili k vytvoření těchto souborů starter pro ovládací prvek, ovládací prvek pro průvodce `DoPropExchange` volání funkce `COleControl::DoPropExchange`. Verze základní třídy vymění uložených vlastností ovládacího prvku; můžete změnit verzi odvozené třídy k vlastnosti serveru exchange, že jste přidali do ovládacího prvku.  
  
 `CPropExchange` slouží k serializaci vlastností ovládacího prvku nebo inicializace vlastností ovládacího prvku při načtení nebo vytvoření ovládacího prvku. `ExchangeProp` a `ExchangeFontProp` členské funkce `CPropExchange` vlastnosti, které chcete ukládat a načítat různá média.  
  
 Další informace o používání `CPropExchange`, najdete v článku [knihovny MFC – ovládací prvky ActiveX: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CPropExchange`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
  
##  <a name="exchangeblobprop"></a>  CPropExchange::ExchangeBlobProp  
 Serializuje vlastnost, která ukládá data binárního rozsáhlého objektu (BLOB).  
  
```  
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,  
    HGLOBAL* phBlob,  
    HGLOBAL hBlobDefault = NULL) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *phBlob*  
 Ukazovat na proměnnou směřující na vlastnosti se mají ukládat (proměnná je obvykle člen třídy).  
  
 *hBlobDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vlastnosti je číst nebo do, případně proměnná odkazuje *phBlob*. Pokud *hBlobDefault* je zadán, použije se jako výchozí hodnota vlastnosti. Tato hodnota se používá, pokud z nějakého důvodu selže serializace ovládacího prvku.  
  
 Funkce `CArchivePropExchange::ExchangeBlobProp`, `CResetPropExchange::ExchangeBlobProp`, a `CPropsetPropExchange::ExchangeBlobProp` čistě virtuální funkci přepsat.  
  
##  <a name="exchangefontprop"></a>  CPropExchange::ExchangeFontProp  
 Vymění vlastnost font mezi střední úložiště a ovládací prvek.  
  
```  
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,  
    CFontHolder& font,  
    const FONTDESC* pFontDesc,  
    LPFONTDISP pFontDispAmbient) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *Písma*  
 Odkaz na [cfontholder –](../../mfc/reference/cfontholder-class.md) objekt, který obsahuje vlastnosti font.  
  
 *pFontDesc*  
 Ukazatel [FONTDESC](/windows/desktop/api/olectl/ns-olectl-tagfontdesc) struktury obsahující hodnoty pro inicializaci výchozí stav vlastností písma při *pFontDispAmbient* má hodnotu NULL.  
  
 *pFontDispAmbient*  
 Ukazatel `IFontDisp` rozhraní písma použitého pro inicializaci výchozí stav vlastností písma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vlastnost písma se načítá z média do ovládacího prvku, vlastností písma se načtou z média a `CFontHolder` objekt odkazovaný zadaným parametrem *písmo* je inicializován s nimi. Pokud je uložen vlastností písma, vlastnosti v objektu písma se zapisují do média.  
  
 Funkce `CArchivePropExchange::ExchangeFontProp`, `CResetPropExchange::ExchangeFontProp`, a `CPropsetPropExchange::ExchangeFontProp` čistě virtuální funkci přepsat.  
  
##  <a name="exchangepersistentprop"></a>  CPropExchange::ExchangePersistentProp  
 Vymění vlastnost mezi ovládacím prvkem a soubor.  
  
```  
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,  
    LPUNKNOWN* ppUnk,  
    REFIID iid,  
    LPUNKNOWN pUnkDefault) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *ppUnk*  
 Ukazatel na proměnnou obsahující ukazatel na vlastnost `IUnknown` rozhraní (Tato proměnná je obvykle člen třídy).  
  
 *identifikátor IID*  
 ID rozhraní na vlastnost, která bude používat ovládací prvek rozhraní.  
  
 *pUnkDefault*  
 Výchozí hodnota pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vlastnost se načítá ze souboru do ovládacího prvku, je vlastnost vytvořen a inicializován ze souboru. Pokud vlastnost ukládají, jeho hodnota zapsána do souboru.  
  
 Funkce `CArchivePropExchange::ExchangePersistentProp`, `CResetPropExchange::ExchangePersistentProp`, a `CPropsetPropExchange::ExchangePersistentProp` čistě virtuální funkci přepsat.  
  
##  <a name="exchangeprop"></a>  CPropExchange::ExchangeProp  
 Vymění vlastnost mezi střední úložiště a ovládací prvek.  
  
```  
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,  
    VARTYPE vtProp,  
    void* pvProp,  
    const void* pvDefault = NULL) = 0 ;  
```  
  
### <a name="parameters"></a>Parametry  
 *pszPropName*  
 Název vlastnosti se vyměňují.  
  
 *vtProp*  
 Symbol závislý na určení typu vlastnosti během výměny. Možné hodnoty jsou:  
  
|Symbol|Typ vlastnosti|  
|------------|-------------------|  
|VT_I2|**short**|  
|VT_I4|**long**|  
|VT_BOOL|**BOOL**|  
|VT_BSTR|`CString`|  
|VT_CY|**CY**|  
|VT_R4|**float**|  
|VT_R8|**double**|  
  
 *pvProp*  
 Ukazatel na hodnotu vlastnosti.  
  
 *pvDefault*  
 Ukazatel na výchozí hodnotu pro vlastnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud bylo úspěšné; exchange 0, pokud není úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vlastnost se načítá z média do ovládacího prvku, hodnota vlastnosti je načtena z média a uloženou v objektu, na které odkazuje *pvProp*. Pokud vlastnost je uloženo na médiu, hodnota objektu, na které odkazuje *pvProp* je zapsán do média.  
  
 Funkce `CArchivePropExchange::ExchangeProp`, `CResetPropExchange::ExchangeProp`, a `CPropsetPropExchange::ExchangeProp` čistě virtuální funkci přepsat.  
  
##  <a name="exchangeversion"></a>  CPropExchange::ExchangeVersion  
 Volá se rozhraním pro zpracování trvalost číslo verze.  
  
```  
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,  
    DWORD dwVersionDefault,  
    BOOL bConvert);
```  
  
### <a name="parameters"></a>Parametry  
 *dwVersionLoaded*  
 Odkaz na proměnnou, kam se má číslo verze trvalého načítají data uložit.  
  
 *dwVersionDefault*  
 Aktuální číslo verze ovládacího prvku.  
  
 *bConvert*  
 Určuje, jestli se má převést trvalá data na aktuální verzi nebo je uchovávejte na stejnou verzi, která byla načtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud se spuštění funkce zdařilo; jinak 0.  
  
##  <a name="getversion"></a>  CPropExchange::GetVersion  
 Voláním této funkce načtete číslo verze ovládacího prvku.  
  
```  
DWORD GetVersion();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Číslo verze ovládacího prvku.  
  
##  <a name="isasynchronous"></a>  CPropExchange::IsAsynchronous  
 Určuje, pokud jsou vlastnost výměny provádět asynchronně.  
  
```  
BOOL IsAsynchronous();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud jsou vlastnosti, které si vyměňují asynchronně, jinak hodnota FALSE.  
  
##  <a name="isloading"></a>  CPropExchange::IsLoading  
 Voláním této funkce určete, jestli se vlastnosti do ovládacího prvku načtení nebo uložení z něj.  
  
```  
BOOL IsLoading();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud vlastnosti jsou načítány; jinak 0.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleControl::DoPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)



