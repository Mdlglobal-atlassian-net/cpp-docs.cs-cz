---
title: Cdberrorinfo – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b7eaba589e729230c0392ac67eff2389d430f842
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465010"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo – třída
Poskytuje podporu pro zpracování chyb technologie OLE DB pomocí rozhraní OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112\(v=vs.85\)) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDBErrorInfo  
``` 

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h 
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetAllErrorInfo](#getallerrorinfo)|Vrátí všechny informace o chybě obsažené v záznamu o chybě.|  
|[GetBasicErrorInfo](#getbasicerrorinfo)|Volání [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907\(v=vs.85\)) vrátit základní informace o zadané chybě.|  
|[GetCustomErrorObject](#getcustomerrorobject)|Volání [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417\(v=vs.85\)) k vrací ukazatel rozhraní na objekt vlastních chyb.|  
|[GetErrorInfo](#geterrorinfo)|Volání [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230\(v=vs.85\)) se vraťte `IErrorInfo` ukazatel rozhraní na zadaný záznam.|  
|[Geterrorparameters –](#geterrorparameters)|Volání [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793\(v=vs.85\)) vrátit parametry chyby.|  
|[GetErrorRecords](#geterrorrecords)|Získá záznamy o chybách pro zadaný objekt.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní vrátí jeden nebo více záznamů chybě uživatele. Volání [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) první zobrazíte počet záznamů chyb. Pak jednu z přístupu funkce, jako volání [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), načíst informace o chybě pro každý záznam.  
  
## <a name="getallerrorinfo"></a> CDBErrorInfo::GetAllErrorInfo
Vrátí všechny typy s informacemi o chybě obsažené v záznamu o chybě.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,  
   LCID lcid,  BSTR* pbstrDescription,  
   BSTR* pbstrSource = NULL,  
   GUID* pguid = NULL,  
   DWORD* pdwHelpContext = NULL,  
   BSTR* pbstrHelpFile = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ulRecordNum*  
 [in] Číslo od nuly záznam, pro které se mají vracet informace o chybě.  
  
 *lcid*  
 [in] ID národního prostředí pro informace o chybě se mají vrátit.  
  
 *pbstrDescription*  
 [out] Ukazatel na textový popis chyby nebo hodnota NULL, pokud není podporované národní prostředí. Viz poznámky.  
  
 *pbstrSource*  
 [out] Ukazatel na řetězec obsahující název komponenty, který vytvořil chybu.  
  
 *pguid*  
 [out] Ukazatel na identifikátor GUID rozhraní definované chyba.  
  
 *pdwHelpContext*  
 [out] Ukazatel na ID kontextové nápovědy k chybě.  
  
 *pbstrHelpFile*  
 [out] Ukazatel na řetězec obsahující cestu k souboru nápovědy, popisující chybu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného ověření. Zobrazit [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230\(v=vs.85\)) v *OLE DB referenční informace pro programátory* pro ostatní vrácené hodnoty.  
  
### <a name="remarks"></a>Poznámky  
 Výstupní hodnota z *pbstrDescription* je interně získán voláním `IErrorInfo::GetDescription`, která nastaví hodnotu na NULL Pokud není podporovaná národní prostředí, nebo pokud jsou splněny obě následující podmínky:  
  
1.  Hodnota *lcid* není USA Angličtina a  
  
2.  Hodnota *lcid* se nerovná hodnotě vrácené GetUserDefaultLCID. 

## <a name="getbasicerrorinfo"></a> CDBErrorInfo::GetBasicErrorInfo
Volání [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907\(v=vs.85\)) vrátit základní informace o této chybě, jako je například návratový kód a číslo chyby specifické pro zprostředkovatele.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,   
   ERRORINFO* pErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  

## <a name="getcustomerrorobject"></a> CDBErrorInfo::GetCustomErrorObject
Volání [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417\(v=vs.85\)) k vrací ukazatel rozhraní na objekt vlastních chyb.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,   
   REFIID riid,IUnknown** ppObject) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  

## <a name="geterrorinfo"></a> CDBErrorInfo::GetErrorInfo
Volání [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230\(v=vs.85\)) se vraťte [IErrorInfo](/previous-versions/windows/desktop/ms718112\(v=vs.85\)) ukazatel rozhraní na zadaný záznam.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,   
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  

## <a name="geterrorparameters"></a> CDBErrorInfo::GetErrorParameters
Volání [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793\(v=vs.85\)) vrátit parametry chyby.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,   
   DISPPARAMS* pdispparams) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  

## <a name="geterrorrecords"></a> CDBErrorInfo::GetErrorRecords
Získá záznamy o chybách pro zadaný objekt.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords) throw();  

HRESULT GetErrorRecords(ULONG* pcRecords) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Rozhraní pro objekt, pro které chcete získat záznamy o chybách.  
  
 *identifikátor IID*  
 [in] Identifikátor IID rozhraní přidružené k chybě.  
  
 *pcRecords*  
 [out] Ukazatel na počet záznamů, chyba (základem 1).  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete zkontrolovat získat informace o chybě, ze které rozhraní, použijte formuláři první funkce. V opačném případě použijte druhý formulář.  
  
## <a name="see-also"></a>Viz také  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)