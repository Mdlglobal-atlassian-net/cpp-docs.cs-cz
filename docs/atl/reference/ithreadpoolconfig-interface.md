---
title: Ithreadpoolconfig – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 156a0a827a67e80369ca8b834b62bcf0e431ab14
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076343"
---
# <a name="ithreadpoolconfig-interface"></a>Ithreadpoolconfig – rozhraní

Toto rozhraní poskytuje metody pro konfiguraci fondu vláken.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetSize](#getsize)|Volejte tuto metodu za účelem získání počet vláken ve fondu.|
|[GetTimeout](#gettimeout)|Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.|
|[SetSize](#setsize)|Voláním této metody nastavte počet vláken ve fondu.|
|[SetTimeout](#settimeout)|Volejte tuto metodu za účelem nastavení maximální doby v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je implementováno [cthreadpool –](../../atl/reference/cthreadpool-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="getsize"></a>  IThreadPoolConfig::GetSize

Volejte tuto metodu za účelem získání počet vláken ve fondu.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
[out] Adresa proměnné, která v případě úspěchu, obdrží počet vláken ve fondu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout

Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
[out] Adresa proměnné, která v případě úspěchu, obdrží maximální dobu v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Zobrazit [IThreadPoolConfig::GetSize](#getsize).

##  <a name="setsize"></a>  IThreadPoolConfig::SetSize

Voláním této metody nastavte počet vláken ve fondu.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Požadovaný počet vláken ve fondu.

Pokud *nNumThreads* je záporný, jeho absolutní hodnota se vynásobí číslo odpovídající počtu procesorů v počítači, chcete-li získat celkový počet vláken.

Pokud *nNumThreads* je nula, ATLS_DEFAULT_THREADSPERPROC bude vynásobené celkovým počtem procesorů v počítači, chcete-li získat celkový počet vláken.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Zobrazit [IThreadPoolConfig::GetSize](#getsize).

##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout

Volejte tuto metodu za účelem nastavení maximální doby v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Maximální požadovaný čas v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Zobrazit [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)<br/>
[CThreadPool – třída](../../atl/reference/cthreadpool-class.md)
