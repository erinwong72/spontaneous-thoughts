# Viewing loss and metrics even when training using train_on_batch
Replace this:
```python
history = model.fit(train_generator, validation_data = (val_x, val_y), epochs = EPOCHS)
```

With this:
```python
callbacks = tf.keras.callbacks.CallbackList(
    None, 
    add_history = True,
    add_progbar = True,
    model = model,
    epochs = EPOCHS,
    verbose = 1,
    steps = len(train_generator)
)

callbacks.on_train_begin()
for epoch in range(EPOCHS):
    model.reset_metrics()
    callbacks.on_epoch_begin(epoch)
    for i in range(len(train_generator)):
        callbacks.on_train_batch_begin(i)
        logs = model.train_on_batch(*train_generator[i], reset_metrics = False, return_dict = True)              
        callbacks.on_train_batch_end(i, logs)

    validation_logs = model.evaluate(val_x, val_y, callbacks = callbacks, return_dict = True)
    logs.update({'val_' + name: v for name, v in validation_logs.items()})

    callbacks.on_epoch_end(epoch, logs)
    train_generator.on_epoch_end()

callbacks.on_train_end(epoch_logs)
history = model.history
```

To account for validation data also being a generator, modify the **evaluate** method, and replace `val_x, val_y` with your validation generator:

```python
def evaluate(self, generator, callbacks=None, return_dict=False):
# for validation
	for i in range(len(generator)):
		callbacks.on_test_batch_begin(i)
		logs = self.test_on_batch(*generator[i], reset_metrics=False, return_dict=return_dict)
		callbacks.on_test_batch_end(i, logs)

return logs
```

---
Source:
[python - Keras: is there sample code for train\_on\_batch which has history + progress? - Stack Overflow](https://stackoverflow.com/questions/65253314/keras-is-there-sample-code-for-train-on-batch-which-has-history-progress)

General sources for the different training methods:
[For large datasets, which to use: fit or train\_on\_batch? · Issue #2708 · keras-team/keras · GitHub](https://github.com/keras-team/keras/issues/2708)
[\`fit\_generator\` and \`train\_on\_batch\` are not well documented and do not work with variable-size inputs · Issue #2539 · keras-team/keras · GitHub](https://github.com/keras-team/keras/issues/2539)