---
title: Rozhraní IThreadPoolConfig
ms.date: 11/04/2016
f1_keywords:
- IThreadPoolConfig
- ATLUTIL/ATL::IThreadPoolConfig
- ATLUTIL/ATL::GetSize
- ATLUTIL/ATL::GetTimeout
- ATLUTIL/ATL::SetSize
- ATLUTIL/ATL::SetTimeout
helpviewer_keywords:
- IThreadPoolConfig interface
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
ms.openlocfilehash: e4b90534fa89ef2aeffe4cd682d92efc16452487
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326361"
---
# <a name="ithreadpoolconfig-interface"></a>Rozhraní IThreadPoolConfig

Toto rozhraní poskytuje metody pro konfiguraci fondu vláken.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
__interface
    __declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660")) IThreadPoolConfig : public IUnknown
```

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[GetSize](#getsize)|Volání této metody získat počet podprocesů ve fondu.|
|[GetTimeout](#gettimeout)|Volání této metody získat maximální čas v milisekundách, že fond vláken bude čekat na vypnutí podprocesu.|
|[Velikost sady](#setsize)|Volání této metody nastavit počet podprocesů ve fondu.|
|[SetTimeout](#settimeout)|Volání této metody nastavit maximální dobu v milisekundách, že fond vláken bude čekat na vypnutí podprocesu.|

## <a name="remarks"></a>Poznámky

Toto rozhraní je implementováno [cthreadpoolem](../../atl/reference/cthreadpool-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="ithreadpoolconfiggetsize"></a><a name="getsize"></a>IThreadPoolConfig::GetSize

Volání této metody získat počet podprocesů ve fondu.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
[out] Adresa proměnné, která při úspěchu obdrží počet podprocesů ve fondu.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/ithreadpoolconfig-interface_1.cpp)]

## <a name="ithreadpoolconfiggettimeout"></a><a name="gettimeout"></a>IThreadPoolConfig::GetTimeout

Volání této metody získat maximální čas v milisekundách, že fond vláken bude čekat na vypnutí podprocesu.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
[out] Adresa proměnné, která při úspěchu obdrží maximální dobu v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Viz [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsetsize"></a><a name="setsize"></a>IThreadPoolConfig::SetSize

Volání této metody nastavit počet podprocesů ve fondu.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Požadovaný počet podprocesů ve fondu.

Pokud *nNumThreads* je záporná, jeho absolutní hodnota se vynásobí počtem procesorů v počítači získat celkový počet podprocesů.

Pokud *nNumThreads* je nula, ATLS_DEFAULT_THREADSPERPROC se vynásobí počtem procesorů v počítači získat celkový počet podprocesů.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Viz [IThreadPoolConfig::GetSize](#getsize).

## <a name="ithreadpoolconfigsettimeout"></a><a name="settimeout"></a>IThreadPoolConfig::SetTimeout

Volání této metody nastavit maximální dobu v milisekundách, že fond vláken bude čekat na vypnutí podprocesu.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Požadovaná maximální doba v milisekundách, po kterou bude fond vláken čekat na vypnutí vlákna.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Viz [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Viz také

[Třídy](../../atl/reference/atl-classes.md)<br/>
[Třída CThreadPool](../../atl/reference/cthreadpool-class.md)
