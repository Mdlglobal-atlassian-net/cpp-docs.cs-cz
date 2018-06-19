---
title: Třída CComGITPtr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
dev_langs:
- C++
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 049873ce6ff630e8f00ea5ad5ec9b3786bd5e71b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363623"
---
# <a name="ccomgitptr-class"></a>CComGITPtr – třída
Tato třída poskytuje metody pro práci s ukazatele rozhraní a globální rozhraní tabulku (GIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class CComGITPtr
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ ukazatele rozhraní se neukládají v GITU.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Konstruktor|  
|[CComGITPtr:: ~ CComGITPtr](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComGITPtr::Attach](#attach)|Volejte tuto metodu za účelem registrace ukazatel rozhraní v tabulce globální rozhraní (GIT).|  
|[CComGITPtr::CopyTo](#copyto)|Volejte tuto metodu pro kopírování rozhraní z tabulky globální rozhraní (GIT) do předaný ukazatele.|  
|[CComGITPtr::Detach](#detach)|Volat tuto metodu pro zrušení přiřazení rozhraní z `CComGITPtr` objektu.|  
|[CComGITPtr::GetCookie](#getcookie)|Volání této metody vrátit soubor cookie z `CComGITPtr` objektu.|  
|[CComGITPtr::Revoke](#revoke)|Voláním této metody rozhraní odebere z tabulky globální rozhraní (GIT).|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](#operator_dword)|Vrátí cookie z `CComGITPtr` objektu.|  
|[CComGITPtr::operator =](#operator_eq)|Operátor přiřazení.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Soubor cookie.|  
  
## <a name="remarks"></a>Poznámky  
 Objekty, které agregace volné zařazování vláken a potřebují používat ukazatele rozhraní získat z jiných objektů, musejí udělat dodatečné kroky k zajištění, že jsou správně zařazeno rozhraní. Obvykle to zahrnuje ukládání ukazatele rozhraní v GITU a získávání ukazatele z GITU pokaždé, když se používá. Třída `CComGITPtr` zajišťuje vám pomohou při použití ukazatele rozhraní, které jsou uložené v GITU.  
  
> [!NOTE]
>  Zařízení tabulky globální rozhraní je dostupná pouze na systém Windows 95 s DCOM verze 1.1 a novější, Windows 98, Windows NT 4.0 s aktualizací Service Pack 3 nebo novější a Windows 2000.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="attach"></a>  CComGITPtr::Attach  
 Volejte tuto metodu za účelem registrace ukazatel rozhraní v tabulce globální rozhraní (GIT).  
  
```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Ukazatel rozhraní mají být přidány do GITU.  
  
 `dwCookie`  
 Soubor cookie použít k identifikaci ukazatel rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 V sestavení pro ladění dojde k chybě assertion Pokud GITU není platný, nebo pokud je soubor cookie rovnou na hodnotu NULL.  
  
##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr  
 Konstruktor  
  
```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `p`  
 Ukazatel rozhraní se neukládají v tabulce globální rozhraní (GIT).  
  
 [v] `git`  
 Odkaz na existující `CComGITPtr` objektu.  
  
 [v] `dwCookie`  
 Soubor cookie použít k identifikaci ukazatel rozhraní.  
  
 [v] `rv`  
 Zdroj `CComGITPtr` pro přesun dat z objektu.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří novou `CComGITPtr` objektu, volitelně pomocí stávající `CComGITPtr` objektu.  
  
 Konstruktor, který využívá `rv` je konstruktor move. Při přesunu dat ze zdroje, `rv`a potom `rv` se vymaže.  
  
##  <a name="dtor"></a>  CComGITPtr:: ~ CComGITPtr  
 Destruktor.  
  
```
~CComGITPtr() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere z tabulky globální rozhraní (GIT), rozhraní pomocí [CComGITPtr::Revoke](#revoke).  
  
##  <a name="copyto"></a>  CComGITPtr::CopyTo  
 Volejte tuto metodu pro kopírování rozhraní z tabulky globální rozhraní (GIT) do předaný ukazatele.  
  
```
HRESULT CopyTo(T** pp) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pp`  
 Ukazatel, což je pro příjem rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní z GITU se zkopíruje na předaný ukazatele. Volající musí vydala ukazatele, pokud se už nevyžaduje.  
  
##  <a name="detach"></a>  CComGITPtr::Detach  
 Volat tuto metodu pro zrušení přiřazení rozhraní z `CComGITPtr` objektu.  
  
```
DWORD Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí cookie z `CComGITPtr` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je až volající rozhraní odebrání GIT, pomocí [CComGITPtr::Revoke](#revoke).  
  
##  <a name="getcookie"></a>  CComGITPtr::GetCookie  
 Volání této metody vrátit soubor cookie z `CComGITPtr` objektu.  
  
```
DWORD GetCookie() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí souboru cookie.  
  
### <a name="remarks"></a>Poznámky  
 Soubor cookie je proměnná používá k identifikaci rozhraní a jeho umístění.  
  
##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie  
 Soubor cookie.  
  
```
DWORD m_dwCookie;
```  
  
### <a name="remarks"></a>Poznámky  
 Soubor cookie je členské proměnné použít k identifikaci rozhraní a jeho umístění.  
  
##  <a name="operator_eq"></a>  CComGITPtr::operator =  
 Operátor přiřazení.  
  
```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `p`  
 Ukazatele na rozhraní.  
  
 [v] `git`  
 Odkaz na `CComGITPtr` objektu.  
  
 [v] `dwCookie`  
 Soubor cookie použít k identifikaci ukazatel rozhraní.  
  
 [v] `rv`  
 `CComGITPtr` Pro přesun dat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí aktualizovaný `CComGITPtr` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Přiřadí novou hodnotu k `CComGITPtr` objekt z existujícího objektu nebo z odkazu na tabulku globální rozhraní.  
  
##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD  
 Vrátí souboru cookie přidruženého `CComGITPtr` objektu.  
  
```  
operator DWORD() const;
```  
  
### <a name="remarks"></a>Poznámky  
 Soubor cookie je proměnná používá k identifikaci rozhraní a jeho umístění.  
  
##  <a name="revoke"></a>  CComGITPtr::Revoke  
 Voláním této metody rozhraní aktuální odebere z tabulky globální rozhraní (GIT).  
  
```
HRESULT Revoke() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěchu nebo chybu HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Odebere rozhraní z GITU.  
  
## <a name="see-also"></a>Viz také  
 [Volné zařazování vláken](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [Přístup k rozhraní mezi Apartment](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [Kdy použít tabulku globální rozhraní](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Přehled třídy](../../atl/atl-class-overview.md)
