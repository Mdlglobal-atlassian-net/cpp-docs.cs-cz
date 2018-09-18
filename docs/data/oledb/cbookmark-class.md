---
title: CBookmark – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7a2eaaf273bb2c0ae4f3ab297fe444a41e81c873
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058053"
---
# <a name="cbookmark-class"></a>CBookmark – třída

Obsahuje hodnotu záložky ve vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
### <a name="parameters"></a>Parametry  

*nSize*<br/>
Velikost vyrovnávací paměti záložek v bajtech. Když *nSize* je nula, vyrovnávací paměti záložek se dynamicky vytvoří za běhu.  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** také atldbcli.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CBookmark](#cbookmark)|Konstruktor|  
|[Getbuffer –](#getbuffer)|Načte ukazatel do vyrovnávací paměti.|  
|[GetSize](#getsize)|Získá velikost vyrovnávací paměti v bajtech.|  
|[SetBookmark](#setbookmark)|Nastaví hodnotu záložku.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#operator)|Přiřadí jednu `CBookmark` třídy na jiný.|  
  
## <a name="remarks"></a>Poznámky  

`CBookmark<0>` je specializací šablony `CBookmark`; vyrovnávací paměti se dynamicky vytvoří za běhu.  

## <a name="cbookmark"></a> CBookmark::CBookmark

Konstruktor  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CBookmark();
   
CBookmark(DBLENGTH nSize);  
```  
  
#### <a name="parameters"></a>Parametry  

*nSize*<br/>
[in] Velikost vyrovnávací paměti záložku v bajtech.  
  
### <a name="remarks"></a>Poznámky  

První funkce nastaví vyrovnávací paměť na hodnotu NULL a velikost vyrovnávací paměti na hodnotu 0. Druhá funkce nastaví velikost vyrovnávací paměti na *nSize*a vyrovnávací paměť do bajtového pole *nSize* bajtů.  
  
> [!NOTE]
>  Tato funkce je dostupná jenom `CBookmark<0>`. 
  
## <a name="getbuffer"></a> CBookmark::GetBuffer

Načte ukazatel na záložku vyrovnávací paměti.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
virtual BYTE* GetBuffer() const throw();  
```  
  
### <a name="return-value"></a>Návratová hodnota  

Ukazatel do vyrovnávací paměti záložku. 

## <a name="getsize"></a> CBookmark::GetSize

Získá velikost vyrovnávací paměti pro záložky.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
virtual DBLENGTH GetSize() const throw();  
```  
  
### <a name="return-value"></a>Návratová hodnota  

Velikost vyrovnávací paměti v bajtech.  

## <a name="setbookmark"></a> CBookmark::SetBookmark

Zkopíruje záložka odkazuje *pBuffer* k `CBookmark` vyrovnávací paměti a nastaví velikost vyrovnávací paměti na *nSize*.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*nSize*<br/>
[in] Velikost vyrovnávací paměti záložek.  
  
*pBuffer*<br/>
[in] Ukazatel na bajtové pole obsahující hodnotu záložku.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Tato funkce je dostupná jenom `CBookmark<0>`. 

## <a name="operator"></a> CBookmark::operator =

Přiřadí `CBookmark` objektu na jiný.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();  
```  
  
### <a name="remarks"></a>Poznámky  

Tento operátor je nutný pouze v `CBookmark<0>`.   

## <a name="see-also"></a>Viz také  

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)