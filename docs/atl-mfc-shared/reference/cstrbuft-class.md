---
title: "Třída CStrBufT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
dev_langs: C++
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8df7f6c1dbd9987a9f83ed5b33a4c97fd90fec7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cstrbuft-class"></a>CStrBufT – třída
Tato třída poskytuje vyčištění automatické prostředků pro `GetBuffer` a `ReleaseBuffer` volání na existující `CStringT` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename TCharType>
class CStrBufT
```  
  
#### <a name="parameters"></a>Parametry  
 *TCharType*  
 Typ znak `CStrBufT` třídy. Může být jedna z následujících akcí:  
  
- `char`(pro znakových řetězců v kódu ANSI)  
  
- `wchar_t`(na řetězec znaků Unicode)  
  
- **Tchar –** (pro ANSI a Unicode řetězce znaků)  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`PCXSTR`|Ukazatel na konstantní řetězec.|  
|`PXSTR`|Ukazatel na řetězec.|  
|`StringType`|Typ řetězec, jehož vyrovnávací paměti je uživatel manipulovat specializací této třídy šablony.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CStrBufT::CStrBufT](#cstrbuft)|V konstruktoru pro vyrovnávací paměť objekt řetězce.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStrBufT::SetLength](#setlength)|Nastaví délka vyrovnávací paměti znak objekt přidružený řetězce.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|Načte **const** ukazatel do vyrovnávací paměti znak objektu přidružené řetězec.|  
|[CStrBufT::operator PXSTR](#operator_pxstr)|Načte ukazatel do vyrovnávací paměti znak objektu přidružené řetězec.|  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[CStrBufT::AUTO_LENGTH](#auto_length)|Automaticky zjistit nový délky řetězce na verzi.|  
|[CStrBufT::SET_LENGTH](#set_length)|Nastavte délku řetězce objektu v době getbuffer –|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída se používá jako obálkovou třídu pro náhradu volání [getbuffer –](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a [ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer), nebo [GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) a `ReleaseBuffer`.  
  
 Primárně určený jako pomocná třída `CStrBufT` představuje pohodlný způsob pro vývojáře pro práci s znak vyrovnávací paměti objektu řetězec bez starostí o nebo kdy se má volat `ReleaseBuffer`. To je možné, protože objekt obálky ocitne mimo obor přirozeně v případě výjimku nebo více cest existujícímu kódu; způsobuje její destruktor na uvolnění prostředků řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpstr.h  
  
##  <a name="auto_length"></a>CStrBufT::AUTO_LENGTH  
 Automaticky zjistit nový délky řetězce na verzi.  
  
```
static const DWORD AUTO_LENGTH = 0x01;
```  
  
### <a name="remarks"></a>Poznámky  
 Automaticky zjistit nový délky řetězce na verzi. Řetězec musí být ukončené hodnotou null.  
  
##  <a name="cstrbuft"></a>CStrBufT::CStrBufT  
 Vytvoří objekt vyrovnávací paměti.  
  
```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Objekt string přidružený vyrovnávací paměti. Vývojář se obvykle používají předdefinované definice TypeDef z **CStrBuf** ( **Tchar –** variant), **CStrBufA** ( `char` variant) a **CStrBufW**  ( `wchar_t` variant).  
  
 *nMinLength*  
 Minimální délka vyrovnávací paměti znak.  
  
 `dwFlags`  
 Určuje, pokud je automaticky určeno délku řetězce. Může být jedna z následujících akcí:  
  
- **AUTO_LENGTH** délka řetězce je automaticky určit, kdy [CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer) je volána. Řetězec musí být ukončené hodnotou null. Výchozí hodnota.  
  
- **SET_LENGTH** délka řetězce je nastavena, když [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) je volána.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří vyrovnávací paměti řetězců pro objekt přidružený řetězce. Během vytváření [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) nebo [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) je volána.  
  
 Všimněte si, že je konstruktor copy `private`.  
  
##  <a name="operator_pcxstr"></a>CStrBufT::operator PCXSTR  
 Přímý přístup k znaky, které jsou uloženy v přidružených řetězec objekt jako řetězec stylu jazyka C.  
  
```  
operator PCXSTR() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Znak ukazatel na data řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se vraťte do vyrovnávací paměti znak objektu string ukazatel. Obsah řetězce objektu nelze změnit pomocí tento ukazatel.  
  
##  <a name="operator_pxstr"></a>CStrBufT::operator PXSTR  
 Přímý přístup k znaky, které jsou uloženy v přidružených řetězec objekt jako řetězec stylu jazyka C.  
  
```
operator PXSTR() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Znak ukazatel na data řetězec.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce se vraťte do vyrovnávací paměti znak objektu string ukazatel. Vývojář může změnit obsah objektu řetězec tento ukazatel.  
  
##  <a name="pcxstr"></a>CStrBufT::PCXSTR  
 Ukazatel na konstantní řetězec.  
  
```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```  
  
##  <a name="pxstr"></a>CStrBufT::PXSTR  
 Ukazatel na řetězec.  
  
```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```  
  
##  <a name="set_length"></a>CStrBufT::SET_LENGTH  
 Nastavte délku řetězce objekt v `GetBuffer` čas.  
  
```
static const DWORD SET_LENGTH = 0x02;
```  
  
### <a name="remarks"></a>Poznámky  
 Getbuffer – okamžiku nastaven délka objekt řetězce.  
  
 Určuje, zda [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer) a [CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength) jsou volány při sestavený objekt řetězce vyrovnávací paměti.  
  
##  <a name="setlength"></a>CStrBufT::SetLength  
 Nastaví délka vyrovnávací paměti znak.  
  
```
void SetLength(int nLength);
```  
  
### <a name="parameters"></a>Parametry  
 `nLength`  
 Nové délka vyrovnávací paměti znak objektu typu string.  
  
> [!NOTE]
>  Musí být menší než nebo rovna minimální velikost vyrovnávací paměti, zadaný v konstruktoru `CStrBufT`.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce lze nastavit délku řetězce reprezentovaný objektem vyrovnávací paměti.  
  
##  <a name="stringtype"></a>CStrBufT::StringType  
 Typ řetězec, jehož vyrovnávací paměti je uživatel manipulovat specializací této třídy šablony.  
  
```
typedef CSimpleStringT<TCharType> StringType;
```  
  
### <a name="remarks"></a>Poznámky  
 **TCharType** je typ znak použitá se specializují šablona třídy.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


