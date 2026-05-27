# Fragmento de Código
router.post("/users", async (req, res) => {
  const { email, password } = req.body;
  if (!email || !password) return res.status(400).send();
  const exists = await db.users.findOne({ email });
  if (exists) return res.status(409).send();
  const user = await db.users.insert({ email, password });
  res.status(201).send(user);
});
