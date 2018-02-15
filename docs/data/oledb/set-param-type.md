---
title: SET_PARAM_TYPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SET_PARAM_TYPE
dev_langs:
- C++
helpviewer_keywords:
- SET_PARAM_TYPE macro
ms.assetid: 85979070-2d55-4c67-94b1-9b9058babc59
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d9cf1ffdc9201a55fcba2cf334c350e924fda113
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="setparamtype"></a>SET_PARAM_TYPE
Určuje `COLUMN_ENTRY` makra, které následují `SET_PARAM_TYPE` makro vstup, výstup nebo vstupu a výstupu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
SET_PARAM_TYPE(type)  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 [v] Typ nastavení parametru.  
  
## <a name="remarks"></a>Poznámky  
 Zprostředkovatelé podporují pouze typy vstupní a výstupní parametr, které jsou podporovány základní zdroj dat. Typ je kombinací jednoho nebo více **DBPARAMIO** hodnoty (viz [DBBINDING struktury](https://msdn.microsoft.com/en-us/library/ms716845.aspx) v *referenční příručka programátora technologie OLE DB*):  
  
-   **DBPARAMIO_NOTPARAM** přistupující objekt nemá žádné parametry. Obvykle nastavíte **eParamIO** na tuto hodnotu v řádku průvodcem upozornit uživatele, že parametry jsou ignorovány na.  
  
-   **DBPARAMIO_INPUT** vstupní parametr.  
  
-   **DBPARAMIO_OUTPUT** výstupní parametr.  
  
-   **DBPARAMIO_INPUT &#124; DBPARAMIO_OUTPUT** parametr je vstupní i výstupní parametr.  
  
## <a name="example"></a>Příklad  
```
cpp  
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
``` 
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)