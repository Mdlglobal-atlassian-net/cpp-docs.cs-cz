---
title: CDataSource::Open | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3196aa89426e895dd6b73b28ce197e8f271a0262
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasourceopen"></a>CDataSource::Open
Otevře připojení k zdroje dat pomocí **CLSID**, **ProgID**, nebo `CEnumerator` přezdívka nebo vyzývá uživatele se dialogové okno lokátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  


HRESULT Open(const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,  
  DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,  
   LPCTSTR pName,  LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(HWND hWnd = GetActiveWindow(),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,   
  DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,   
   LPCTSTR pName,LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsid`  
 [v] **CLSID** zprostředkovatele dat.  
  
 *pPropSet*  
 [v] Ukazatel na pole [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury obsahující vlastnosti a hodnoty nastavení. V tématu [sady vlastností a vlastnost skupiny](https://msdn.microsoft.com/en-us/library/ms713696.aspx) v *referenční příručka programátora prostředí OLE DB* ve Windows SDK.  
  
 *nPropertySets*  
 [v] Počet [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury předaná *pPropSet* argument.  
  
 *pName*  
 [v] Název databáze, ke kterému chcete připojit.  
  
 *pUserName*  
 [v] Jméno uživatele.  
  
 *pPassword*  
 [v] Heslo uživatele.  
  
 `nInitMode`  
 [v] Režim inicializaci databáze. V tématu [inicializační vlastnosti](https://msdn.microsoft.com/en-us/library/ms723127.aspx)v *referenční příručka programátora technologie OLE DB* ve Windows SDK pro seznam režimů platný inicializace. Pokud `nInitMode` je nula, žádné inicializace režimu je součástí sady vlastností, které se používá k otevření připojení.  
  
 `szProgID`  
 [v] Identifikátor programu.  
  
 `enumerator`  
 [v] A [CEnumerator](../../data/oledb/cenumerator-class.md) objekt použitý k získání Přezdívka pro otevření připojení, pokud má volající neurčuje **CLSID**.  
  
 `hWnd`  
 [v] Popisovač okna, které má být nadřazená dialogového okna. Pomocí funkce přetížení, které používá `hWnd` parametr automaticky vyvolá součásti služby; podrobnosti naleznete v části poznámky.  
  
 `dwPromptOptions`  
 [v] Určuje styl Lokátor dialogové okno pro zobrazení. Možné hodnoty najdete v části Msdasc.h.  
  
## <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT`.  
  
## <a name="remarks"></a>Poznámky  
 Přetížení metody, která používá `hWnd` parametr otevře objekt zdroje dat s součásti služby v oledb32.dll; tento soubor DLL obsahuje implementace funkce součásti služby, například sdílení prostředků ve fondech, automatické zařazení transakce a tak dále. Další informace najdete v tématu "OLE DB služby" v OLE DB referenční informace pro programátory v [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
 Přetížení metody, které nepoužívají `hWnd` parametr otevřít objekt zdroje dat bez použití součásti služby v oledb32.dll. A [CDataSource](../../data/oledb/cdatasource-class.md) objekt otevřít pomocí těchto přetížení funkce se nebude moci využívat všechny funkce součásti služby.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak otevřít zdroj dat a Jet 4.0 s šablonami technologie OLE DB. Zdroj dat Jet se považovat za zdroj dat OLE DB. Ale volání **otevřete** potřebuje dvě sady vlastností: jeden pro **DBPROPSET_DBINIT** a druhou pro **DBPROPSET_JETOLEDB_DBINIT**, takže můžete nastavit  **DBPROP_JETOLEDB_DATABASEPASSWORD**.  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDataSource – třída](../../data/oledb/cdatasource-class.md)
