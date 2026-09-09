Original:
modifier[socket_id] = value

Changed to:
getattr(modifier.properties.inputs, socket_id).value = value
