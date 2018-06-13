<?php

namespace App\Console\Commands;

use App\Mail\TestingMail;
use Illuminate\Console\Command;
use Illuminate\Support\Facades\Mail;
use Illuminate\Support\Facades\Redis;

class SendQueueEmail extends Command
{
    /**
     * The name and signature of the console command.
     *
     * @var string
     */
    protected $signature = 'command:SendQueueEmail';

    /**
     * The console command description.
     *
     * @var string
     */
    protected $description = 'Worker Untuk Send Queue Email Pake Redis Biasa';

    /**
     * Create a new command instance.
     *
     * @return void
     */
    public function __construct()
    {
        parent::__construct();
    }

    /**
     * Execute the console command.
     *
     * @return mixed
     */
    public function handle()
    {
        $list_queue_email = Redis::SMEMBERS('send_email');

        foreach($list_queue_email as $queue){
            $queueConvert = json_decode($queue);
            $this->info("Sending email to {$queue}");

            //send email
            Mail::to($queueConvert->email)->send(new TestingMail());
            //sampai sini

            $delete_queue_email = Redis::SREM('send_email', $queue);
            $this->info('Delete data email {$delete_queue_email}');
        }
    }
}
