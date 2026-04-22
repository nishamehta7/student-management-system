use App\Mail\AnnouncementPosted;
use Illuminate\Http\Request;
use App\Models\Announcement;
use Carbon\Carbon;
use Illuminate\Support\Facades\Mail;

class TeacherAnnouncementController extends Controller
{
public function index()
{
        return view('pages.teachers.announcements.index', ['announcements' => auth()->user()->teacher->announcements]);
        $announcements = auth()->user()->teacher->announcements;
        $today = Carbon::today();
        $yesterday = Carbon::yesterday();

        $todayAnnouncements = $announcements->filter(function ($announcement) use ($today) {
            return $announcement->created_at->isSameDay($today);
        });

        $yesterdayAnnouncements = $announcements->filter(function ($announcement) use ($yesterday) {
            return $announcement->created_at->isSameDay($yesterday);
        });

        $otherAnnouncements = $announcements->filter(function ($announcement) use ($today, $yesterday) {
            return !$announcement->created_at->isSameDay($today) && !$announcement->created_at->isSameDay($yesterday);
        });

        return view('pages.teachers.announcements.index', compact('todayAnnouncements', 'yesterdayAnnouncements', 'otherAnnouncements'));
}

public function create()
