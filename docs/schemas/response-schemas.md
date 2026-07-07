# Response Schemas

## CompaniesList

**Endpoints**:

1. <code>GET /api/companies</code>
2. <code>GET /api/issues/companies</code>

```json
{
    "type": "object",
    "properties": {
        "data": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "company_id": {
                        "type": "integer"
                    },
                    "company_name": {
                        "type": "string"
                    },
                    "company_address": {
                        "type": "string"
                    },
                    "company_status": {
                        "type": "string",
                        "enum": [
                            "ACTIVE",
                            "CLOSED",
                            "BANKRUPT"
                        ]
                    }
                },
                "required": [
                    "company_id",
                    "company_name",
                    "company_address",
                    "company_status"
                ],
                "additionalProperties": false
            }
        },
        "meta": {
            "type": "object",
            "properties": {
                "total": {
                    "type": "integer"
                },
                "limit": {
                    "type": [
                        "integer",
                        "null"
                    ]
                },
                "offset": {
                    "type": [
                        "integer",
                        "null"
                    ]
                }
            },
            "required": [
                "total"
            ],
            "additionalProperties": false
        }
    },
    "required": [
        "data",
        "meta"
    ],
    "additionalProperties": false
}
```

## CompanyWithAllowedLanguage

**Endpoints**: 

1. <code>GET /api/companies/{company_id}</code>
2. <code>GET /api/issues/companies/{company_id}</code>

```json
{
    "type": "object",
    "properties": {
        "company_id": {
            "type": "integer"
        },
        "company_name": {
            "type": "string"
        },
        "company_address": {
            "type": "string"
        },
        "company_status": {
            "type": "string",
            "enum": [
                "ACTIVE", 
                "CLOSED", 
                "BANKRUPT"
            ]
        },
        "description": {
            "type": "string"
        }
    },
    "required": [
        "company_id",
        "company_name",
        "company_address",
        "company_status",
        "description"
    ],
    "additionalProperties": false    
}
```

## CompanyWithNonAllowedLanguage

**Endpoints**: 

1. <code>GET /api/companies/{company_id}</code>
2. <code>GET /api/issues/companies/{company_id}</code>

```json
{
    "type": "object",
    "properties": {
        "company_id": {
            "type": "integer"
        },
        "company_name": {
            "type": "string"
        },
        "company_address": {
            "type": "string"
        },
        "company_status": {
            "type": "string",
            "enum": [
                "ACTIVE", 
                "CLOSED", 
                "BANKRUPT"
            ]
        },
        "description_lang": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "translation_lang": {
                        "type": "string"
                    },
                    "translation": {
                        "type": "string"
                    }
                },
                "required": [
                    "translation_lang",
                    "translation"
                ],
                "additionalProperties": false
            }
        }
    },
    "required": [
        "company_id",
        "company_name",
        "company_address",
        "company_status",
        "description_lang"
    ],
    "additionalProperties": false   
}
```

## ErrorDetail

**Endpoints**: 

1. <code>GET /api/companies/{company_id}</code>
2. <code>POST /api/users</code>
3. <code>GET /api/users/{user_id}</code>
4. <code>PUT /api/users/{user_id}</code>
5. <code>DELETE /api/users/{user_id}</code>
6. <code>GET /api/issues/companies/{company_id}</code>
7. <code>GET /api/issues/users/{user_id}</code>

```json
{
    "type": "object",
    "properties": {
        "detail": {
            "type": "object",
            "properties": {
                "reason": {
                    "type": "string"
                }
            },
            "required": [
                "reason"
            ],
            "additionalProperties": false
        }
    },
    "required": [
        "detail"
    ],
    "additionalProperties": false
}
```

## HTTPValidationError

**Endpoints**: 

1. <code>GET /api/companies</code>
2. <code>GET /api/companies/{company_id}</code>
3. <code>GET /api/users</code>
4. <code>POST /api/users</code>
5. <code>GET /api/users/{user_id}</code>
6. <code>PUT /api/users/{user_id}</code>
7. <code>DELETE /api/users/{user_id}</code>
8. <code>GET /api/issues/companies</code>
9. <code>GET /api/issues/companies/{company_id}</code>
10. <code>GET /api/issues/users/{user_id}</code>
11. <code>POST /api/issues/users</code>

```json
{
    "type": "object",
    "properties": {
        "detail": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "type": {
                        "type": "string"
                    },
                    "loc": {
                        "type": "array",
                        "items": {
                            "type": [
                                "string", 
                                "integer"
                            ]
                        }
                    },
                    "msg": {
                        "type": "string"
                    }
                },
                "required": [
                    "type",
                    "loc",
                    "msg"
                ],
                "additionalProperties": true
            }
        }
    },
    "required": [
        "detail"
    ],
    "additionalProperties": false
}
```

## UsersList

**Endpoints**: 

1. <code>GET /api/users</code>

```json
{
    "type": "object",
    "properties": {
        "meta": {
            "type": "object",
            "properties": {
                "total": {
                    "type": "integer"
                },
                "limit": {
                    "type": [
                        "integer", 
                        "null"
                    ]
                },
                "offset": {
                    "type": [
                        "integer", 
                        "null"
                    ]
                }
            },
            "required": [
                "total"
            ],
            "additionalProperties": false
        },
        "data": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "first_name": {
                        "type": [
                            "string", 
                            "null"
                        ]
                    },
                    "last_name": {
                        "type": "string"
                    },
                    "company_id": {
                        "type": [
                            "integer", 
                            "null"
                        ]
                    },
                    "user_id": {
                        "type": "integer"
                    }
                },
                "required": [
                    "last_name",
                    "user_id"
                ],
                "additionalProperties": false
            }
        }
    },
    "required": [
        "meta",
        "data"
    ],
    "additionalProperties": false
}
```

## ResponseUser

**Endpoints**: 

1. <code>POST /api/users</code>
2. <code>GET /api/users/{user_id}</code>
3. <code>PUT /api/users/{user_id}</code>
4. <code>GET /api/issues/users/{user_id}</code>
5. <code>POST /api/issues/users</code>

```json
{
    "type": "object",
    "properties": {
        "first_name": {
            "type": [
                "string", 
                "null"
            ]
        },
        "last_name": {
            "type": "string"
        },
        "company_id": {
            "type": [
                "integer", 
                "null"
            ]
        },
        "user_id": {
            "type": "integer"
        }
    },
    "required": [
        "last_name",
        "user_id"
    ], 
    "additionalProperties": false
}
```
## DeleteUserResponse

**Endpoints**: 

1. <code>DELETE /api/users/{user_id}</code>

```json
{
    "type": "object",
    "additionalProperties": true
}
```
