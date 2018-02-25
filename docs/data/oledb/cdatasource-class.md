---
title: "CDataSource – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
dev_langs:
- C++
helpviewer_keywords:
- CDataSource class
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 508bbfc7551383fe1d4517d274031faef590fdb9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="cdatasource-class"></a>CDataSource – třída
OLE DB datový objekt, který reprezentuje prostřednictvím poskytovatele připojení ke zdroji dat odpovídá.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CDataSource  
```  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zavřete](../../data/oledb/cdatasource-close.md)|Ukončí připojení.|  
|[Getinitializationstring –](../../data/oledb/cdatasource-getinitializationstring.md)|Načte inicializačního řetězce zdroje dat, který je aktuálně otevřený.|  
|[GetProperties –](../../data/oledb/cdatasource-getproperties.md)|Získá hodnoty pro připojených zdrojů dat aktuálně nastaveny vlastnosti.|  
|[GetProperty](../../data/oledb/cdatasource-getproperty.md)|Získá hodnotu vlastnosti jediné nastaveno pro připojeného zdroje dat.|  
|[Open](../../data/oledb/cdatasource-open.md)|Vytvoří připojení k poskytovateli (zdroj dat) buď pomocí **CLSID**, **ProgID**, nebo `CEnumerator` Přezdívka poskytnutá volajícím.|  
|[OpenFromFileName](../../data/oledb/cdatasource-openfromfilename.md)|Otevře se zdroji dat ze souboru určeného název souboru zadaný uživatelem.|  
|[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)|Otevře se zdroji dat určeného inicializačního řetězce.|  
|[OpenWithPromptFileName](../../data/oledb/cdatasource-openwithpromptfilename.md)|Umožňuje uživateli vybrat soubor odkazu na dříve vytvořenou dat otevřít odpovídající zdroj dat.|  
|[OpenWithServiceComponents](../../data/oledb/cdatasource-openwithservicecomponents.md)|Otevře objekt zdroje dat pomocí dialogového okna dat propojení.|  
  
## <a name="remarks"></a>Poznámky  
 Pro jednoho připojení můžete vytvořit jeden nebo více relací databáze. Tyto relace jsou reprezentované pomocí `CSession`. Je třeba volat [CDataSource::Open](../../data/oledb/cdatasource-open.md) k otevření připojení před vytvořením relace s `CSession::Open`.  
  
 Příklad použití `CDataSource`, najdete v článku [ukázky CatDB](../../visual-cpp-samples.md) ukázka.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)