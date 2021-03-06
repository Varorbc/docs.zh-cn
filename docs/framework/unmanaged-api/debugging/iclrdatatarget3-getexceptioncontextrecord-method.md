---
title: ICLRDataTarget3::GetExceptionContextRecord 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
ms.openlocfilehash: 3e73d0fc48dcfeafb3fe2f23ec07cdc04a561a9e
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860450"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord 方法
由公共语言运行时 (CLR) 数据访问服务调用，以检索与目标进程关联的上下文记录。 例如，对于转储目标，此操作等效于通过 Windows 调试帮助库（Dbghelp.dll）中的`ExceptionParam` [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump)函数的参数传入的上下文记录。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>参数  
 `bufferSize`  
 [in] 输入缓冲区大小（以字节为单位）。 此大小必须大到足以容纳上下文记录。  
  
 `bufferUsed`  
 [out] 指向接收实际写入缓冲区的字节数的 `ULONG32` 类型的指针。  
  
 `buffer`  
 [out] 指向接收上下文记录副本的内存缓冲区的指针。 异常记录作为[上下文](/windows/win32/api/winnt/ns-winnt-arm64_nt_context)类型返回。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回值是 `S_OK`；如果失败，则返回失败 `HRESULT` 代码。 `HRESULT` 代码可以包括但不限于以下代码：  
  
|返回代码|说明|  
|-----------------|-----------------|  
|`S_OK`|方法成功。 已将上下文记录复制到输出缓冲区。|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|没有与目标关联的上下文记录。|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|输入缓冲区大小不足以容纳上下文记录。|  
  
## <a name="remarks"></a>备注  
 [上下文](/windows/win32/api/winnt/ns-winnt-arm64_nt_context)是在 Windows SDK 提供的标头中定义的特定于平台的结构。  
  
 此方法由调试应用程序的编写器实现。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** ClrData，ClrData  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICLRDataTarget3 接口](iclrdatatarget3-interface.md)
- [GetExceptionRecord 方法](iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID 方法](iclrdatatarget3-getexceptionthreadid-method.md)
