# 测试 RNN + queue 能否提速

## 实验结果

不使用Queue: 0m51.097s
单个线程：0m44.573s
两个线程：0m45.963s
四个线程：0m46.690s

## Details

Queue 启动的两种方法：

    qr = tf.train.QueueRunner(queue, [enqueue_op] * num_threads)
(1)
    queue_threads = qr.create_threads(sess = sess, coord = coord, start = True)
(2)
    tf.train.add_queue_runner(qr)
    queue_threads = tf.train.start_queue_runners(sess = sess, coord = coord)
