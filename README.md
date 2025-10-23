# 通用接口调用示例文档
> 示例接口地址与字段仅用于教学目的。

---

## 📘 接口概览

* **接口名称**：内容点赞操作（示例）
* **请求方法**：`POST`
* **接口地址**：`https://www-hj.douyin.com/aweme/v1/web/commit/item/digg/ 或者https://www.douyin.com/aweme/v1/web/commit/item/digg/`
* **请求类型**：`application/x-www-form-urlencoded`
* **编码格式**：UTF-8

---

## 🧾 请求参数说明

| 参数名               | 类型     | 必填 | 示例值                   | 说明                |
| :---------------- | :----- | :- | :-------------------- | :---------------- |
| `aweme_id`        | string | ✅  | `6933566366121315597` | 内容唯一 ID           |
| `item_type`       | int    | ✅  | `0`                   | 内容类型标识            |
| `type`            | int    | ✅  | `1`                   | 操作类型（1=点赞，0=取消点赞） |
| `msToken`         | string | ✅  | `xxx`                 | 安全凭证，用于身份验证       |
| `device_platform` | string | ✅  | `webapp`              | 请求来源平台            |
| `aid`             | string | ✅  | `6383`                | 应用标识              |

---

## 🧠 调用示例（Java）

```java
public ApiResult likeVideo(String awemeId, int operationType) {
    try {
        String uifid = extractCookieField(cookies, "UIFID");
        if (uifid.isEmpty()) {
            String temp = extractCookieField(cookies, "UIFID_TEMP");
            if (!temp.isEmpty()) uifid = temp;
        }

        String url = "https://www-hj.douyin.com/aweme/v1/web/commit/item/digg/";
        Map<String,String> params = new LinkedHashMap<>();
        params.put("msToken", msToken);
        params.put("device_platform", "webapp");
        params.put("aid", "6383");
        params.put("channel", "channel_pc_web");
        params.put("version_code", "170400");
        params.put("os_name", "Windows");
        params.put("uifid", uifid);

        // body: x-www-form-urlencoded
        Map<String,String> body = new HashMap<>();
        body.put("aweme_id", awemeId);
        body.put("item_type", "0");
        body.put("type", String.valueOf(operationType));

        String form = toForm(body);
        String response = HttpUtil.post(url, params, form);
        return ApiResult.success(response);
    } catch (Exception e) {
        return ApiResult.error(e.getMessage());
    }
}
```

---

## ⚙️ 响应示例

```json
{success=true, data={"status_code":0,"is_digg":0,"extra":{"now":1761184547000,"fatal_item_ids":[],"logid":"2025102309554641B98F1FA272102D6966"},"log_pb":{"impr_id":"2025102309554641B98F1FA272102D6966"}}, message='点赞成功'}
```

---

---

## 🧩 附录：常用参数建议

* **超时时间**：建议设置 `connectTimeout=30s`，`readTimeout=30s`
* **重试机制**：最多重试 3 次，延迟 1s-3s
* **日志记录**：建议打印响应体和耗时
* **异常捕获**：捕获 `IOException` 和 `SocketTimeoutException`

---

## 📞 联系方式

如需学习交流或技术探讨，可通过以下方式联系：

* ✈️ 飞机号：[https://t.me/fajxhdnnsh](https://t.me/fajxhdnnsh)
* 💬 QQ：3189475980

---

> 📎 **免责声明**：
> 本文档仅供学习 HTTP 请求结构、参数构造与 Java 网络请求逻辑使用。请勿将示例用于任何未授权的平台或行为。
